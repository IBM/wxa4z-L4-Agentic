# Deploy Agent Service

1. Next, deploy the `AgentService` by customizing the `workload-scheduler-agent-z/cr.yaml` file that you downloaded. 

    Modify the following values:

    - `metadata.namespace` : `wxa4z-agents`

    - `spec.namepsace`: `wxa4z-agents`
   
    - `spec.tenantId` : *set to your [tenant id](../setup.md#record-your-tenant_id)*

    - `WATSONX_MODEL_ID` : *your model id*

    - `MODEL_RUNTIME` : `cloud`

    - `AIOPS_BASE_URL` : *set to same URL value as set in previous section*
    
    - `ZCHATOPS_MCP_URL` : `https://zchatops-workload-wxa4z-aiops-33.wsc-ocp-watsonx-showcase-b0cdb30d4dd4f32c05cec1804800ef26-0000.us-east.containers.appdomain.cloud`


2. Once modified, deploy the `AgentService` by running the following command:

    `oc apply -f cr.yaml`


3. Verify it was deployed successfully by navigating to the `wxa4z-agents` namespace in your OpenShift cluster .
   
    You should see the pod running.


4. Click on the pod logs and make sure you see "agent registered successfully"
