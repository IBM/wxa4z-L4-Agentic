# Deploying the Token Exchange service for PassTicket generation

## Overview

The Token Exchange service runs directly on the z/OS system and is responsible for generating one-time-use PassTickets. Each PassTicket is uniquely created by securely combining a user's email ID with an application ID, ensuring that every request is tied to a specific user and application context.
To ensure secure access, the service is not exposed to other services and agents directly. Instead, it is accessible only through an intermediary authorization service. Communication between the token exchange service and the authorization service is secured using mutual Transport Layer Security (mTLS), which establishes a bidirectional, cryptographically verified trust. This ensures that only authenticated and trusted services can interact with the token exchange service to request PassTickets.

**The below steps provide a quick procedure for:**

1. Associating user email addresses with a RACF ID on zD&T
2. Starting the Token Exchange Service on zD&T

**NOTE:** For the full step-by-step instructions, reference the IBM Docs page: https://www.ibm.com/docs/en/watsonx/waz/3.2.0?topic=deploying-token-exchange-service-passticket-generation

The provisioned zD&T image on TechZone has completed most of the setup work for you. The below steps will illustrate how to configure. 


### Adding "Passticket users" to RACF 

Once the Token Exchange Service is started (in the next step), users who have been added to a mapped RACF identity are authenticated against their registered email address (recorded by watsonx Orchestrate).

This scenario illustrates how to associate two users' email addresses with a pre-created RACF ID on zD&T (`IBMUSER`). For security purposes, it's strongly recommended to create individual RACF ID's per user, and associated their email address with each's ID. 

1. First, access the `TSO commmand utility` or any interface for issuing TSO commands to the zD&T image. 
   
    For example, using **Option 6** in an ISPF session:

    ![](_attachments/auth1.png)

2. For each user who will be accessing agents via watsonx Orchestrate, you will associate their email address to the `IBMUSER` RACF ID for demo purposes and ease of setup. 

    As an example, say we have two users with email addresses:

    - `johndoe@ibm.com`
    - `janesmith@ibm.com`

    First, create the identity filter that maps the `johndoe@ibm.com` user to the `IBMUSER` RACF ID using the following command:

    ```
    RACMAP ID(IBMUSER) MAP USERDIDFILTER(NAME('johndoe@ibm.com')) REGISTRY(NAME('LDAPS://BLUEPAGES.IBM.COM')) WITHLABEL('JOHN DOE')
    ```

3. Next, create the identity filter for the `janesmith@ibm.com` user to the same `IBMUSER` RACF ID:
   
    
    ```
    RACMAP ID(IBMUSER) MAP USERDIDFILTER(NAME('janesmith@ibm.com')) REGISTRY(NAME('LDAPS://BLUEPAGES.IBM.COM')) WITHLABEL('JANE SMITH')
    ```

    IMPORTANT: It's crucial that the `WITHLABEL` value be unique for each user. 

4. Finally, for RACF to recognize the mapping profile, the `IDIDMAP` general resource profile must be refreshed. 
    
    Run the following RACF command via TSO:

    ```
    SETROPTS RACLIST(IDIDMAP) REFRESH
    ```

5. To verify the successful mapping, you can then run the command:
   
    ```
    RACMAP ID(IBMUSER) LISTMAP
    ```

    ![](_attachments/auth2.png)


### Start the Token Exchange Service

Now that you have user identities mapped to RACF, you can start the **Token Exchange Service**. As previously mentioned, most of the setup has been done on the templated zD&T image. All that's needed is to run a UNIX shell command on z/OS USS. 

The easiest way to do this is to SSH directly into z/OS Unix System Services...

1. SSH into your zD&T's USS by following the steps in ***[this previous section](./techzone/zdt.md#ssh-into-zos-unix-system-services)***.

2. From the UNIX Shell, navigate to the `/u/ibmuser/token` directory by issuing:
  
    `cd token`
    
    ![](_attachments/auth3.png)

3. Finally, **start** the token exchange service by issuing the following command:
   
    ```
    nohup java -jar token-exchange-mtls.jar &
    ```

    ![](_attachments/auth4.png)

    **NOTE:** it will take some time...

4. After waiting a few minutes, verify that **port 5444** on the zD&T image is open and reachable - this is the port configured for the token exchange service. 
   
    This can be done using the following options:

    **a.)** SSH into z/OS USS from a new session and issue the `netstat` command

    Verify that port `5444` is listening as shown below:

    ![](_attachments/auth5.png)

      **b.)** From your machine's local command-prompt, issue the following command (substituting `<public ip>` with the public IP address of your own zD&T image):

      ```
      nc -zv <public ip> 5444
      ```

      If working, you should get output similar to:

      `Connection to 52.118.145.999 port 5444 [tcp/*] succeeded!`


### Optional Testing

Once the Token Exchange Service is up and running, you can verify the authentication by following the below steps. 

#### Step 1: Register a mock agent

1. First, **retrieve the route** of your environment's **authorization service** by logging into your OpenShift Web Console UI, and navigating to **Routes** under the **Networking** panel, then copy and pasting the Route **Location** for the `wxa4z-authorization-route` as shown below:
  
    **IMAGE**

2. Secondly record the endpoint URL of your zD&T's running Token Exchange Service. To do this:
   
   **a.)** Navigate to the environment details for your **zD&T** environment on TechZone:

   **IMAGE**

   **b.)** At the bottom of your reservation details, you should see your `Hostname` as shown in the screenshot below. Copy and paste that value to a local notepad.

   **IMAGE**

   **c.)** Record the following value using the `Hostname` you previously recorded:

   ```
   https://<Hostname>.techzone.ibm.com:5444
   ```

   In the above example, my final endpoing URL would be:

   `https://itzvsi-550000kksb-pmjtc8cl.techzone.ibm.com:5444`

3. Register a mock agent using the following CURL command from your local machine's command terminal/prompt, replacing `<auth route>` with your authorization route recorded in step 1, and replacing `<token endpoint>` with the endpoint URL of your zD&T's Token exchange service recorded in step 2 above:
   
    ```
    curl --request PUT \
    --url <auth route>/api/v1/agents/wxa4z:cics:agent \
    --header 'Authorization: !cicsagent@' \
    --header 'Content-Type: application/json' \
    --header 'User-Agent: insomnia/11.4.0' \
    --data '{ "service_endpoint":"<token endpoint>" }'
    ```

4. Using the above example, the command and associated output would be:
   
    ```
    curl --request PUT \
    --url https://wxa4z-authorization-route-wxa4z-zad.apps.itz-9m4n0h.hub01-lb.techzone.ibm.com/api/v1/agents/wxa4z:cics:agent \
    --header 'Authorization: !cicsagent@' \
    --header 'Content-Type: application/json' \
    --header 'User-Agent: insomnia/11.4.0' \
    --data '{ "service_endpoint":"https://itzvsi-550000kksb-pmjtc8cl.techzone.ibm.com:5444" }'
    ```

    The expected output should be something similar to:

    ```
    {"message":"Agent registered successfully","register_at":"2026-05-16T06:47:28Z"}
    ```

### Step 2: Retrieve Token

Next, retrieve the token value that will be used as input for generating a passticket for your user. 

Run the following CURL command from your local mcahine's command terminal/prompt, replacing `<auth route>` with your authorization service route recorded earlier:

```
curl --request GET \
--url <auth route>/api/v1/agents/wxa4z:cics:agent/token \
--header 'Authorization: !cicsagent@' \
--header 'accept: application/json' 
```

The expected output should be the value of an `access-token` as shown in the example below. Copy and record the value of your token as you'll need it later. 

```
{"access-token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhZ2VudF9pZCI6Ind4YTR6OmNpY3M6YWdlbnQiLCJpc3MiOiJhdXRob3JpemF0aW9uIiwic3ViIjoid3hhNHo6Y2ljczphZ2VudCIsImV4cCI6MTc3ODkxNzc1NSwiaWF0IjoxNzc4OTE0MTU1fQ.DF_7sg_pbJu3vRen3caqN5izSIBm_grFlgOSDdoU4Hs"}%
```

### Step 3: Generate Passticket

Run the below command to generate a passticket for a user, replacing the following values:

- `<auth route>`: replace with the route of your authorization service recorded earlier
- `<token>`: replace with the token value outputted in previous command
- `<EMAIL_ID>`: replace with one of the email addresses used for mapping the two previous fictitious users to RACF (i.e. `johndoe@ibm.com` or `janesmith@ibm.com`).

```
curl --request POST \
  --url <auth route>/api/v1/agents/wxa4z:cics:agent/passticket \
  --header 'Authorization: Bearer <token>' \
  --header 'Content-Type: application/json' \
  --header 'accept: application/json' \
  --data '{   "applid": "IZUDFLT",   "emailid": "<EMAIL_ID>" }'
```

For example:

```
curl --request POST \
  --url https://wxa4z-authorization-route-wxa4z-zad.apps.itz-9m4n0h.hub01-lb.techzone.ibm.com/api/v1/agents/wxa4z:cics:agent/passticket \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhZ2VudF9pZCI6Ind4YTR6OmNpY3M6YWdlbnQiLCJpc3MiOiJhdXRob3JpemF0aW9uIiwic3ViIjoid3hhNHo6Y2ljczphZ2VudCIsImV4cCI6MTc3ODkxNzc1NSwiaWF0IjoxNzc4OTE0MTU1fQ.DF_7sg_pbJu3vRen3caqN5izSIBm_grFlgOSDdoU4Hs' \
  --header 'Content-Type: application/json' \
  --header 'accept: application/json' \
  --data '{   "applid": "IZUDFLT",   "emailid": "johndoe@ibm.com" }'
```

The expected output should be something similar to:

```
{"token":"CKBW9X1S","token_type":"passticket","zos_userid":"IBMUSER","email":"johndoe@ibm.com"}
```
