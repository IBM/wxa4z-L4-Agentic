# Deploy required secrets for OpenSearch and Client Ingestion

In this step you will create the required secrets and other pre-configuration for the **zAssistantDeploy services**. For all of the instructions in this section, it is assumed that you’re accessing your local command line or terminal prompt in the ***zAssistDeploy*** directory.

### OpenSearch

OpenSearch enables you to search, analyze, and visualize large volumes of data in real time. 

1. In your downloaded/extracted ***zAssistDeploy*** directory, there is an `os-secret.yaml` file. In a text editor of your choice (i.e.command-line,VSCode,etc.),modify this file to replace `<OPENSEARCH_PASSWORD>` with a secure password of your choice (and save it). 
   
    ***Record this value for later use.***
    
    ![](_attachments/secrets1.png)

2. Create the secret by running the following command within the same directory:
   
    ```
    oc apply -f os-secret.yaml
    ```
   
### Content Ingestion

Customers can ingest their content into the search database to improve the AI Assistant’s ability to retrieve information from their uploaded documents, in addition to leveraging IBM documentation.

1. Modify the `client-ingestion-secret.yaml` file, replacing `<CLIENT_INGESTION_AUTHKEY>` with a 
secure authentication key of your choosing (i.e. a password). 

    ***Record this value for later use.***

    ![](_attachments/secrets2.png)

2. Create the secret by running the following command within the same directory:
   
    ```
    oc apply -f client-ingestion-secret.yaml
    ```
   

### Authorization service

The Authorization service ensures secure access by validating the current login user in watsonx Orchestrate® against the z/OS User Management system.

- A user logs into and interacts with the Z AI agent.

- watsonx Orchestrate sends the user’s email ID to the Z AI agent , which forwards it to the Authorization Service.

- The Authorization Service queries the z/OS User Management system to verify the user’s permissions.

- The z/OS system responds, either granting or denying access based on the user's credentials.

    **PLACEHOLDER**


### z/OS Topology Service

The **z/OS Topology Service** serves as a central repository for managing the topology of z/OS systems. 

1. Modify the `wxa4z-zos-topology-secrets.yaml` file with the secret values for your system. Open the file in a text editor of your choice.

    You should see the following with placeholders:

    ```
    ZOSMF_USERNAME: "<value>"
    ZOSMF_PASSWORD: "<value>"
    OMEGAMON_TOKEN: "<value>"
    REDIS_PASSWORD: "<value>"
    ```

2. Replace the **value** for `ZOSMF_USERNAME` with **IBMUSER**


3. Replace the **value** for `ZOSMF_PASSWORD` with a unique password/passphrase value that the **IBMUSER** ID uses to log into TSO. 

    To set your new Password value, follow the steps outlined ***[here](../agentdeploy/upgrade-agent/secrets-data.md#set-your-zosmf_password-variable)***. 

4. Once modified and saved, create the secret by running the following command:
   
    ```
    oc apply -f wxa4z-zos-topology-secrets.yaml
    ```

### Wrapper secret

1. Next, modify the `wrapper-creds.yaml` file, replacing `<WRAPPER_PASSWORD>` with a secure password credential. **Record this value for later use as this is what you’ll later use to configure your assistant and agent OpenSearch connection.**
   
    ![](_attachments/secrets3.png)

2. Create the secret by running the following command within the same directory:
   
    ```
    oc apply -f wrapper-creds.yaml
    ```

### Create IFM Secret

#### PLACEHOLDER




