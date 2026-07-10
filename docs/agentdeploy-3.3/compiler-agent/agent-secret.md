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
      AGENT_AUTH_TOKEN: ""
      LANGFUSE_SECRET_KEY: ""
      LANGFUSE_PUBLIC_KEY: ""
    ```

2. Modify the following variables:
   
    - Set `metadata.namespace` to `wxa4z-agents`
  
    - Set `AGENT_AUTH_TOKEN` to any string of your choice for registration with WxO. 

3. Once done, apply the secret by running:


    `oc apply -f compiler-secret.yaml`

4. If not already created, you must create the `tz-pull-secret` secret in the `wxa4z-agents` namespace to deploy this agent. 
   
    Retrieve the <a href="https://ibm.box.com/s/7sm5v6nfzrm7r0vz64zyb81cmgx1x40e" target="_blank">entitlement key here</a>.

    Then run the following command, replacing `<entitlement-key>` with the value you copied:

    ```
    oc -n wxa4z-agents create secret docker-registry tz-pull-secret --docker-server=us.icr.io --docker-username=iamapikey --docker-password=<entitlement-key>
    ```

