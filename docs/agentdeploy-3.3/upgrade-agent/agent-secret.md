# Create agent-specific secret

1. Now create the agent-specific secret for the **IBM Z Upgrade Agent** by copying the following to a file called `upgrade-secret.yaml`:

    ```
    apiVersion: v1
    kind: Secret
    metadata:
        name: upgrade-agent-secrets
        namespace: "wxa4z-agents"
    type: Opaque
    stringData:
        AGENT_AUTH_TOKEN: "" 
        ZOSMF_ENDPOINT: ""
        ZOSMF_USERNAME: "" 
        ZOSMF_PASSWORD: ""
        INIT_KEY: "test"
    ```


1. Modify the following variables:
   
    - Set `metadata.namespace` to `wxa4z-agents`
  
    - Set `AGENT_AUTH_TOKEN` to any string of your choice for registration with WxO. 

    - Set `AIOPS_BASE_URL` to the value found <a href="https://ibm.box.com/s/8o7x1zi9rxs5nrejla9ld6rhf1ek0sab" target="_blank">here.</a>

    - Set `AIOPS_TOKEN` to the value found <a href="https://ibm.box.com/s/8o7x1zi9rxs5nrejla9ld6rhf1ek0sab" target="_blank">here.</a>

2. Once done, apply the secret by running:


    `oc apply -f omegamon-secret.yaml`