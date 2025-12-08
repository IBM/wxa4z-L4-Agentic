# Configuring the `secrets.data` variables

Scrolling down further in the **IBM Z Upgrade Agent** section of your `values.yaml` file, you will see a **`secrets.data`** section with additional variables you must configure. It will look like what’s shown below:

```
secrets:
  data:
    ENCRYPT_KEY: ""
    AGENT_AUTH_TOKEN: ""
```

The below table describes each of the variables in the `secrets.data` variables section. The rows with default values can be set to what's shown in the `Default value to set` column. The rows without default values are unique to your environment and will require you to set that value using the instructions below in this section. 


**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**ENCRYPT_KEY** | Encrypt key for storing confidential information in mongodb metadata store | -------
**AGENT_AUTH_TOKEN** | Token used by the agent-controller to register this agent with WxO | "db2_auth_token"


**ACTION:** Set the **default** variable values for the rows above in your `values.yaml` file:


### Generate an *ENCRYPT_KEY* secret 

Follow the below steps to generate the **Encrypt Key** to set for the `ENCRYPT_KEY` variable.

1. In your VS Code Terminal session, ensure you have the **python** or **python3** tool installed. 

2. Install the **cryptography** command-line tool by running one of the following commands:
   
    `pip install cryptography`

    `pip3 install cryptography`

3. Once installed, start a python terminal by running `python` or `python3` in your VS Code terminal.
   
    **IMAGE**

4. Generate your encrypt key by copying the following lines and pasting in your Python terminal.
   
    ```
    from cryptography.fernet import Fernet
    Fernet.generate_key()
    ```
    
    The result should look similar to the following:

    **IMAGE**

5. Copy the string in single-quotes to your `ENCRYPT_KEY` variable. For example:
   
    **IMAGE**
