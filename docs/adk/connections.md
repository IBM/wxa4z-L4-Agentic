# Creating a connection and configuring credentials

### Creating a connection

Within watsonx Orchestrate and the ADK, a **connection** represents a dependency on an external service. It is a common feature needed in many parts of the ADK, such as tools and knowledge bases. Connections provide a way to associate various tools together and assigning credentials needed for the tools to access external services on behalf of the agent.

In this Lab, the tools you will use are focused on calling APIs exposed by Ansible Automation Platform in order to retrieve certificate information and renew certificates. So before you create any tools, you must create a connection for the tools to use with the assigned credentials for AAP.

When using the ADK, connections are created using YAML specification files. More details on those specifications can be found ***<a href="https://developer.watson-orchestrate.ibm.com/connections/build_connections" target="_blank">here</a>***.

For this Lab, there is a `connections.yaml` file pre-created for you within the `Connections` sub-folder of your VS Code workspace. This file specifies the following:

- `app-id: ansible`
    - Unique identifier for the connection
- `environments: draft`
    - Defines settings for the draft environment before you later deploy the agent
- `kind: basic`
    - Connection type used to access the AAP service (username & password)
- `type: team`
    - the credentials will apply to all users
- `sso: false`
    - not required for 'basic' connections
- `server_url: <AAP UI URL>`
    - The URL of your AAP instance which ***you will replace in the following steps***

1. Within VS Code, click on the `connections.yaml` file in the *Connections* sub-folder to view the contents within VS Code.
   
    **IMAGE**

2. Once the file is opened, edit the file to **replace** `<AAP UI URL>` with the URL of your AAP environment that you recorded earlier.
   
    *For example:*

    **IMAGE**

    ***Note:*** *the URL you paste will be unique and not the same as what's shown above. 

3. Make sure to **save** the file after modifying it.

4. Now you can import the connection to your ADK environment by. 
   
    In the VS Code **Terminal** window, run the following command and then click **enter**:

    ```
    orchestrate connections import --file Connections/connections.yaml
    ```

5. You should then receive a success message as shown below:
   
    **IMAGE**

6. Now verify the connection was successfully created by running the following command in your VS Code Terminal session:
   
    ```
    orchestrate connections list
    ```

7. In the output of the command, notice that your new connection is listed with *app-id* `ansible` and that the Credentials have not yet been set (as shown below).
   
    *Note: you may need to scroll to the top of the connections list*

    **IMAGE**

    You will next set your connection credentials in the following section.

### Setting your connection credentials

You will now set connection credentials to later authenticate tools to access your external AAP environment and automate tasks.

Credentials hold the values used to authorize against external services. In the case of your previously created connection, you configured it with kind: basic which enforces username and password credentials (i.e. the username and password used to login to AAP).

**ACTION:** Take note of and record the values of your `AAP User Name (for UI access)` and `AAP User Password` used to log into your AAP environment's web console. For a reminder on how to retrieve these values, you can reference ***Section [Accessing the environment](../techzone/aap-zos.md#accessing-the-environment)***. 

*You will need these credentials for the following step.*

1. Set an environment variable for your `AAP User Password` value by running the below command (depending on your operating system):
   
    ***MacOS Users:***
    ```
    export aap_password="<your AAP User Password>"
    ```

    ***Windows Users:***
    ```
    set aap_password="<your AAP User Password>"
    ```

2. To set your connection credentials, copy and paste the following command into your VS Code Terminal session and click **enter**:
   
    ***MacOS Users:***
    ```
    orchestrate connections set-credentials --app-id ansible --env draft --username admin --password $aap_password
    ```

    ***Windows Users:***
    ```
    orchestrate connections set-credentials --app-id ansible --env draft --username admin --password %aap_password%
    ```

3. You should see a `Credentials successfully set...` message as shown below:
   
    **IMAGE**

4. Now re-verify the connection with your newly set credentials by entering the following command in your command-line and clicking **enter**:
   
    ```
    orchestrate connections list
    ```

5. You should now see that your previous connection now has credentials set, as shown below:
   
    **IMAGE**