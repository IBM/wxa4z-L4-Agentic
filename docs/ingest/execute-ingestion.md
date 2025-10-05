# Execute Document Ingestion

In this step you will log into your **client ingestion server** and kickoff the ingestion pipeline for your uploaded files.

1. Navigate to your local command-prompt or Terminal window and set the **WXA4Z_TLS_VERIFY** environment variable to **false** to skip server certificate verification by running the following command (depending on your operating system):

    ***Mac users:***
    ```
    export WXA4Z_TLS_VERIFY=false
    ```

    ***Windows users:***
    ```
    set WXA4Z_TLS_VERIFY=false
    ```

    ***Windows PowerShell Users:***
    ```
    Set-Item Env:\WXA4Z_TLS_VERIFY “false”
    ```

2. Retrieve the **Server URL** for your Client Ingestion Server.

    ***Mac users:***
    ```
    echo https://$(oc -n wxa4z-zad get route wxa4z-client-ingestion -o jsonpath="{.spec.host}")
    ```

    ***Windows users (this method can also be used by Mac users):***
    You can retrieve the URL in your OCP Web console by navigating to **Networking -> Routes**, and then copy the URL for the **wxa4z-client-ingestion** route as shown below:

    **IMAGE**

3. Retrieve the **client-ingestion-authkey** for your Client Ingestion server by running the following command: 
   
    ```
    oc -n wxa4z-zad get secret client-ingestion-authkey -o jsonpath="{.data.authkey}" | base64 -d
    ```
    
    The output of this command is your unique **auth-key** that you had previously set. You will need the output of both previous commands in the next step.

    !!! Warning "If the command doesn't work for you"

        If the command doesn't work for you, you can find the **authkey** value by viewing the ***client-ingestion-secret.yaml*** file you modified, and copying the value set for the ***authkey*** parameter. 


4. Log into your client ingestion server using the **zassist** utility by running the following command, replacing `<server_url>` with the value from **step 2** above:

    ```
    zassist login <server_url>
    ```

5. When prompted, enter the **authkey** value from **step 3** above. Then verify that a **Success** message is returned. 

6. Verify that you're connected by running the following command:

    ```
    zassist list
    ```

    This command will return all connected remote sources to your client ingestion server. By default, you should see in the output that there are no connected sources under `ID`.

7. Start the ingestion process to connect your remote COS source to the watsonx Assistant for Z data ingestion pipeline by running the following command (***see below the command on how to retrieve each of the parameters listed***):

    ```
    zassist ingest s3 "<SOURCE_NAME>" "<S3_URL>" "<S3_KEY_ID>" "<S3_SECRET_KEY>" "<BUCKET_NAME>" --watch --skip-pii
    ```

    **a**. **<SOURCE_NAME\>** : replace this with any name of your choice. Make sure the name is in lowercase, uses only underscores, and does not start with a number. 

    **b**. **<S3_URL\>**: 

     - To retrieve your `<S3_URL>`, navigate to your **COS instance** in IBM Cloud 
     - Click on the **Endpoints** tab on the left-hand menu:
    
         **IMAGE**
        
     - In the **'Select resiliency'** drop-down, select **Regional**: 
  
         **IMAGE**
    
     - In the ‘**Select location**’ drop-down click on the region where you created your bucket. In the example shown earlier, the bucket was created in the **eu-de** region, so you would select the **Europe – Frankfurt (eu-de)** region as shown below.
  
         **IMAGE**

        ***Make sure to select the region that corresponds to your own bucket***



