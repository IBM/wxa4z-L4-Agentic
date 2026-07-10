# Setup for Agent deployment

## Create `wxa4z-agents` namespace

For the purpose of the TechZone environment, we will create a new namespace, called `wxa4z-agents` which will be used for all other agent deployments, versus deploying in the previously created tenant namespace. 

Create the namespace by running the following command:

```
oc create namespace wxa4z-agents
```

## Record your `tenant_id`

During agent deploying and creating the **Global agent secrets**, you'll need to provide your `tenant_id`. This can be located in two places:

1. In your watsonx Orchestrate **Service Instance URL**, the `tenant_id` appears as the final string at the end of the URL. For example:
   
    ```
    https://api.us-south.watson-orchestrate.cloud.ibm.com/instances/<tenant_id>
    ```
   
2. In your OpenShift web UI, the tenant namespace that automatically gets created contains the value of your tenant id (i.e. `wxa4z-<tenant_id>`). 

Copy and record the `tenant_id` for your environment as this wil be used next. 


## Create Global tenant secret

1. Copy and paste the following into a new file in your current directory, called `global-secrets.yaml`:

    ```
    apiVersion: v1
    kind: Secret
    metadata:
      name: wxa4z-watsonx-credentials
      namespace: wxa4z-agents
    type: Opaque
    stringData:
      ORCHESTRATE_ENV_TYPE: ""
      CPD_INSTANCE_API_KEY: "" 
      ORCHESTRATE_ENV_URL: "" 
      CPD_USERNAME: "" 
      WATSONX_DEPLOYMENT_SPACE_ID: "" 
      WATSONX_ML_URL: "" 
      EXTERNAL_WATSONX_API_KEY: "" 
      WATSONX_PROJECT_ID: ""
      LANGFUSE_HOST: ""
      LANGFUSE_SECRET_KEY: ""
      LANGFUSE_PUBLIC_KEY: ""
      MODEL_RUNTIME: "cloud" 
      LLM_BASE_URL: ""
      LLM_API_KEY: "" 
      WRAPPER_URL: ""
      WRAPPER_PASSWORD: "" 
      WRAPPER_USERNAME: "" 
      INGESTION_PASSWORD: "" 
      INGESTION_URL: ""
      TENANT_ID: ""
    ```

2. Modify the following values as described below:
   
    - `ORCHESTRATE_ENV_TYPE`
        - Set to `ibm_iam` for **IBM Cloud**

    - `CPD_INSTANCE_API_KEY`
        - Set this to the value of your **API key** that you generated in the IBM Cloud console and recorded in Section ***[Generate IBM Cloud API key](../watsonx-ai/api-key.md)***.


    - `ORCHESTRATE_ENV_URL`
        - Set this to the full URL of your watsonx Orchestrate Service Instance URL which you recorded in Section ***[Retrieve watsonx Orchestrate Service Instance URL](../watsonx-ai/service-instance-url.md)***.

    - `CPD_USERNAME`
        - leave empty string
    
    - `WATSONX_DEPLOYMENT_SPACE_ID`
        - Set this to your **Deployment Space ID** you recorded in Section ***[Create Deployment Space](../watsonx-ai/deployment-space.md)***.

    - `WATSONX_ML_URL`
        - Set this to the URL (region dependent) that you recorded in Section ***[Locate your WML Base URL](../watsonx-ai/wml-base-url.md)***.

    - `EXTERNAL_WATSONX_API_KEY`
        - Set this to the value of your **API key** that you generated in the IBM Cloud console and recorded in Section ***[Generate IBM Cloud API key](../watsonx-ai/api-key.md)***.

    - `WATSONX_PROJECT_ID`
        - Set this to your **Project ID** you created and recorded in Section ***[Create watsonx.ai Project](../watsonx-ai/project.md)***.

    - `MODEL_RUNTIME`
        - Set this to `cloud`

    - `LLM_BASE_URL`
        - Leave empty string

    - `LLM_API_KEY`
        - Leave empty string

    - `WRAPPER_URL`
        - Set this to the **network route** of your `opensearch-wrapper-<tenantid>` pod in your tenant namespace (`wxa4z-<tenantid>`), appending `/v1/query` at the end of the URL.

    - `WRAPPER_PASSWORD`
        - Set this to the value of the `WRAPPER_PASSWORD` key in the `wxa4z-watsonx-credentials` secret in the tenant namespace (`wxa4z-<tenantid>`)

    - `WRAPPER_USERNAME`
        - Set this to the value of the `WRAPPER_USERNAME` key in the `wxa4z-watsonx-credentials` secret in the tenant namespace (`wxa4z-<tenantid>`)

    - `INGESTION_PASSWORD`
        - Set this to the value of the `INGESTION_PASSWORD` key in the `wxa4z-watsonx-credentials` secret in the tenant namespace.

    - `INGESTION_URL`
        - Set this to the value of the `INGESTION_URL` key in the `wxa4z-watsonx-credentials` secret in the tenant namespace.

    - `TENANT_ID`
        - Set this to the `tenant_id` value you recorded [earlier](./setup.md#record-your-tenant_id).


3. Once the values have been modified and file saved, apply the global secret by running the following command:
   
    ```
    oc apply -f global-secrets.yaml
    ```

## Setup deployment charts

Finally, down the <a href="https://ibm.box.com/s/5q0bokvtkg1gh0snk0u8axwz4z9jb301" target="_blank">z-ai-agents-v3.3 charts here</a> that contain the agent service CR's for each of the agents you will be deploying. 

For each of the agents you deploy, you must first create the **Agent-specific secret** in the  `wxa4z-agents` namespace. Reference the official `z-ai-agents` Helm charts for details on those values. 

After creating the agent-specific secret, you then create the `AgentService` custom resource, using the `cr.yaml` files provided above. 

Once the `AgentService` is created, you can **subscribe** the agent which deploys it in watsonx Orchestrate where it is then available for use. These steps will be covered in this section per-agent. 