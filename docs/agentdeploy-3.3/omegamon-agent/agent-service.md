# Deploy Agent Service

Next, deploy the `AgentService` by customizing the `omegamon-insight-agent-z/cr.yaml` file that you downloaded. 

Modify the following values:

- `metadata.namespace` : `wxa4z-agents`
- `spec.tenantId` : *set to your tenant id*
- `WATSONX_MODEL_ID` : *your model id*
- `MODEL_RUNTIME` : `cloud`
- `AIOPS_BASE_URL` : *set to same URL value as set in previous section*
- `ZCHATOPS_MCP_URL` : `https://zchatops-omegamon-zchatops-32.wsc-ocp-watsonx-showcase-b0cdb30d4dd4f32c05cec1804800ef26-0000.us-east.containers.appdomain.cloud`


Once modified, deploy the `AgentService` by running the following command:

`oc apply -f cr.yaml`

## Verify agent deployment