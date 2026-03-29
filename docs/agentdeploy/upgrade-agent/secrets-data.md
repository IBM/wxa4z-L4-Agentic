# Configuring the `secrets.data` variables

Scrolling down further in the **IBM Z Upgrade Agent** section of your `values.yaml` file, you will see a **`secrets.data`** section with additional variables you must configure. It will look like what’s shown below:

```
secrets:
  data:
    ZOSMF_ENDPOINT: ""
    ZOSMF_USERNAME: ""
    ZOSMF_PASSWORD: ""
    AGENT_AUTH_TOKEN: ""
    WRAPPER_USERNAME: ""
    WRAPPER_PASSWORD: ""
    INGESTION_PASSWORD: ""
```

The below table describes each of the variables in the `secrets.data` variables section. The rows with default values can be set to what's shown in the `Default value to set` column. The rows without default values are unique to your environment and will require you to set that value using the instructions below in this section. 


**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**ZOSMF_ENDPOINT** | Endpoint URL for z/OSMF, provided by IBM for managing and interacting with z/OS systems. | -------
**ZOSMF_USERNAME** | User ID for connecting to the z/OSMF endpoint | "IBMUSER"
**ZOSMF_PASSWORD** | Password/Passphrase for connecting to the z/OSMF endpoint | -------
**AGENT_AUTH_TOKEN** | Authentication token used to register the agent with WxO | "upgrade_auth_token"
**WRAPPER_USERNAME** | Username for accessing the WRAPPER_URL endpoint | "admin"
**WRAPPER_PASSWORD** | Password for accessing the WRAPPER_URL endpoint | -------
**INGESTION_PASSWORD** | Password for accessing the INGESTION_URL endpoint | -------

**ACTION:** Set the **default** variable values for the rows above in your `values.yaml` file:

* `ZOSMF_USERNAME: "IBMUSER"`
* `AGENT_AUTH_TOKEN: "upgrade_auth_token"`
* `WRAPPER_USERNAME: "admin"`

### Set your `ZOSMF_ENDPOINT` variable

Now you will set the `ZOSMF_ENDPOINT` variable to the unique z/OSMF endpoint URL of your **zD&T** image environment. This can be gathered by following the steps in ***Section [Accessing z/OSMF Web-UI](../../techzone/zdt.md#accessing-zosmf-web-ui)***.

### Set your `ZOSMF_PASSWORD` variable

Set the `ZOSMF_PASSWORD` variable to a new RACF Password/Passphrase that the IBMUSER ID uses to log into TSO. 

If you haven't already, create a new **RACF Passphrase** for your `IBMUSER` ID and set it to the value for your `ZOSMF_PASSWORD` variable. This can be done by following the steps in ***Section [Set new Passphrase for IBMUSER](../../techzone/zdt.md#set-new-passphrase-for-ibmuser)***.


### Set your `WRAPPER_PASSWORD` variable

Set the **`WRAPPER_PASSWORD`** variable to the `<WRAPPER_PASSWORD>` value you set in your **wrapper-creds.yaml** file in Section ***[Deploy secrets for OpenSearch and Client Ingestion](../../zAssistantDeploy/deploy-secrets.md)***.

### Set your `INGESTION_PASSWORD` variable

Finally, set the `INGESTION_PASSWORD` variable to the **authkey** value you set in your **client-ingestion-secret.yaml** file in Section ***[Deploy secrets for OpenSearch and Client Ingestion](../../zAssistantDeploy/deploy-secrets.md)***.