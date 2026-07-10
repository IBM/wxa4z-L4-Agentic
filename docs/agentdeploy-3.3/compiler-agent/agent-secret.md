# Create agent-specific secret

1. Now create the agent-specific secret for the **IBM Z Compilers Fix Finder Agent** by copying the following to a file called `compiler-secret.yaml`:


    ```
    apiVersion: v1
    kind: Secret
    metadata:
      name: wxa4z-compiler-fix-finder-agent-secrets
      namespace: ""
    type: Opaque
    stringData:
      AGENT_AUTH_TOKEN: "comp_auth"
      LANGFUSE_SECRET_KEY: ""
      LANGFUSE_PUBLIC_KEY: ""
    ```

2. Modify the following variables:
   
    - Set `metadata.namespace` to `wxa4z-agents`
  
    - Set `AGENT_AUTH_TOKEN` to any string of your choice for registration with WxO. 

3. Once done, apply the secret by running:


    `oc apply -f compiler-secret.yaml`