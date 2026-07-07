# Create agent-specific secret

Now create the agent-specific secret for the **IBM Z OMEGAMON Insights Agent** by copying the following to a file called `omegamon-secret.yaml`:

```
apiVersion: v1
kind: Secret
metadata:
  name: wxa4z-omegamon-insights-agent-secrets
  namespace: "" 
type: Opaque
stringData:
  # Agent Authentication (base64-encoded, REQUIRED)
  AGENT_AUTH_TOKEN: "" 
  AIOPS_BASE_URL: ""
  # AIOps Configuration (base64-encoded, optional)
  AIOPS_TOKEN: ""
```

Set `metadata.namespace` to `wxa4z-agents`

Set `AGENT_AUTH_TOKEN` to any string of your choice for registration with WxO. 

Set `AIOPS_BASE_URL` to the value found <a href="https://ibm.box.com/s/8o7x1zi9rxs5nrejla9ld6rhf1ek0sab" target="_blank">here.</a>

Set `AIOPS_TOKEN` to the value found <a href="https://ibm.box.com/s/8o7x1zi9rxs5nrejla9ld6rhf1ek0sab" target="_blank">here.</a>

Once done, apply the secret by running:

`oc apply -f omegamon-secret.yaml`