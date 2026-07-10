# Deploy Agent Service

1. Next, deploy the `AgentService` by customizing the `upgrade-agent-cr.yaml` file that you downloaded. 

    Modify the following values:

    - `metadata.namespace` : `wxa4z-agents`

    - `spec.namepsace`: `wxa4z-agents`
   
    - `spec.tenantId` : *set to your [tenant id](../setup.md#record-your-tenant_id)*

    - `HOST_NAME`:
    - `WATSONX_MODEL_ID`
    - `MODEL_RUNTIME`
    - `PDS_NAME`
    - `CLIENT_INGESTION_STARTUP`
    - `AUTH_TYPE`
    - `ZOSMF_ENDPOINT`
    - `LLM_MODEL`
    - `AGENT_API_KEY`
    - `ZOSMF_USERNAME`
    - `ZOSMF_PASSWORD`
    - `SMPNTS`
    - `SMPWDIR`
    - `SMPJHOME`
    - `SMPCPATH`
    - `ORDER_SERVER_URL`
    - `KEYRING`
    - `CERT_NAME`
    - `DOWNLOAD_METHOD`
    - `DOWNLOADKEYRING`
    - `SIGNATUREKEYRING`


2. Once modified, deploy the `AgentService` by running the following command:

    `oc apply -f cr.yaml`


3. Verify it was deployed successfully by navigating to the `wxa4z-agents` namespace in your OpenShift cluster .
   
    You should see the pod running as shown below:

    **IMAGE**


4. Click on the pod logs and make sure you see "agent registered successfully"

