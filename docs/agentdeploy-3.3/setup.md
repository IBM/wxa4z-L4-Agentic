# Setup for Agent deployment

## Create `wxa4z-agents` namespace


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

## Setup deployment charts




- download charts with 
  - secret
  - CR
  - subscription
- create wxa4z-agents namespace
- create global-secrets.yaml file

