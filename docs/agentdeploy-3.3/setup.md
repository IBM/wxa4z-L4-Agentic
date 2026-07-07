# Setup for Agent deployment

## Create `wxa4z-agents` namespace

For the purpose of the TechZone environment, we will create a new namespace, called `wxa4z-agents` which will be used for all other agent deployments, versus deploying in the previously created tenant namespace. 

Create the namespace by running the following command:

`oc create namespace wxa4z-agents`

## Create Global tenant secret

1. Copy and paste the following into a new file in your current directory, called `global-secrets.yaml`:

    ```
    apiVersion: v1
    kind: Secret
    metadata:
      name: wxa4z-watsonx-credentials
      namespace: wxa4z-zad
    type: Opaque
    stringData:
      ORCHESTRATE_ENV_TYPE: "ibm_iam" # Set to "cpd" or "ibm_iam" (for IBM Cloud)
      CPD_INSTANCE_API_KEY: "" # CPD API key or IBM Cloud IAM API key
      ORCHESTRATE_ENV_URL: "" # WXO service instance URL
      CPD_USERNAME: "" # CPD username for on-premises deployments
      WATSONX_DEPLOYMENT_SPACE_ID: "" # Watsonx deployment space ID
      WATSONX_ML_URL: "" # CPD instance FQDN for on-premises deployments
      EXTERNAL_WATSONX_API_KEY: "" # CPD instance API key for connect
      WATSONX_PROJECT_ID: "" # Watsonx project ID
      LANGFUSE_HOST: ""
      LANGFUSE_SECRET_KEY: ""
      LANGFUSE_PUBLIC_KEY: ""
      MODEL_RUNTIME: "cloud" # "cpd", "cloud", or "openai_protocol"
      LLM_BASE_URL: "" # Inferencing stack URL when MODEL_RUNTIME is openai_protocol
      LLM_API_KEY: "" # Inferencing stack API key when MODEL_RUNTIME is openai_protocol
      WRAPPER_URL: ""
      WRAPPER_PASSWORD: "" # Desired wrapper password
      WRAPPER_USERNAME: "" # Desired wrapper username
      INGESTION_PASSWORD: "" # Desired client ingestion password
      INGESTION_URL: ""
      TENANT_ID: ""
    ```

2. Modify the above values according to your needs, then apply the global secret by running the following command from the same directory:
   
    ```
    oc apply -f global-secrets.yaml
    ```

## Setup deployment charts

Finally, download the charts here that contain the agent service CR's for each of the agents you will be deploying. 

For each of the agents you deploy, you must first create the **Agent-specific secret** in the  `wxa4z-agents` namespace. Reference the official `z-ai-agents` Helm charts for details on those values. 

After creating the agent-specific secret, you then create the `AgentService` custom resource, using the `cr.yaml` files provided above. 

Once the `AgentService` is created, you can **subscribe** the agent which deploys it in watsonx Orchestrate where it is then available for use. These steps will be covered in this section per-agent. 