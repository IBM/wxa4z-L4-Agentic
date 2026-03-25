# Creating a connection and configuring credentials

### Creating a connection

Within watsonx Orchestrate and the ADK, a **connection** represents a dependency on an external service. It is a common feature needed in many parts of the ADK, such as tools and knowledge bases. Connections provide a way to associate various tools together and assigning credentials needed for the tools to access external services on behalf of the agent.

In this Lab, the tools you will use are focused on calling **z/OSMF APIs** to your zD&T zOS image in order to issue various diagnostic commands and retrieve system details. So before you import any tools, you must create a connection for the tools to use with the credentials for your zD&T image.

When using the ADK, connections are created using YAML specification files. More details on those specifications can be found ***<a href="https://developer.watson-orchestrate.ibm.com/connections/build_connections" target="_blank">here</a>***.

For this Lab, there is a `zosmf_connection.yaml` file pre-created for you. This file specifies the following:

- `app-id: zosmf`
    - Unique identifier for the connection
- `environments: draft`
    - Defines settings for the draft environment before you later deploy the agent
- `kind: basic`
    - Connection type used to access the z/OSMF REST APIs (username & password)
- `type: team`
    - the credentials will apply to all users
- `sso: false`
    - not required for 'basic' connections
- `server_url: https://<public-ip>:10443/zosmf/`
    - The URL endpoint for your z/OSMF instance which ***you will modify in the following steps***

1. Within VS Code, click on the `zosmf_connection.yaml` file to view the contents within VS Code.
   
    ![](_attachments/conn1.png)

2. Once the file is opened, edit the file to **replace** `<public-ip>` in the `server_url` variable with the **public IP of your zD&T environment reservation**. 
   
    **NOTE:** this can be found by following the steps in ***Section [Accessing the environment](../../techzone/zdt.md#accessing-the-environment)***.
   
    *For example:*

    ![](_attachments/conn2.png)

    ***Note:*** *the URL you paste will be unique and not the same as what's shown above. 

3. Make sure to **save** the file after modifying it.

4. Now you can import the connection to your ADK environment.
   
    In the VS Code **Terminal** window, run the following command and then click **enter**:

    ```
    orchestrate connections import --file zosmf_connection.yaml
    ```

5. You should then receive a success message as shown below:
   
    ![](_attachments/conn3.png)

6. Now verify the connection was successfully created by running the following command in your VS Code Terminal session:
   
    ```
    orchestrate connections list
    ```

7. In the output of the command, notice that your new connection is listed with *app-id* `zosmf` and that the Credentials have not yet been set (as shown below).
   
    *Note: you may need to scroll to the top of the connections list*

    ![](_attachments/conn4.png)

    You will next set your connection credentials in the following section.

### Setting your connection credentials

You will now set connection credentials to later authenticate tools to access your environment's z/OSMF APIs.

Credentials hold the values used to authorize against external services. In the case of your previously created connection, you configured it with kind: basic which enforces username and password credentials (i.e. the username and password used by the z/OS `IBMUSER` ID).

**ACTION:** Record/relocate the RACF Passphrase you set for **IBMUSER** in ***Section [Set new Passphrase for IBMUSER](../../techzone/zdt.md#set-new-passphrase-for-ibmuser)***.

*You will need these credentials for the following step.*

1. To set your connection credentials, enter the following command into your VS Code Terminal and click **enter**, replacing `<your-passphrase>` with the value of the RACF Passphrase you set earlier for **IBMUSER**:
   
    ```
    orchestrate connections set-credentials --app-id zosmf --env draft --username IBMUSER --password '<your-passphrase>'
    ```

    For example:

    ```
    orchestrate connections set-credentials --app-id zosmf --env draft --username IBMUSER --password 'YOUR PASSWORD PHRASE'
    ```


2. You should see a `Credentials successfully set...` message as shown below:
   
    ![](_attachments/conn5.png)

3. Now re-verify the connection with your newly set credentials by entering the following command in your command-line and clicking **enter**:
   
    ```
    orchestrate connections list
    ```

4. You should now see that your previous connection now has credentials set, as shown below:
   
    ![](_attachments/conn6.png)