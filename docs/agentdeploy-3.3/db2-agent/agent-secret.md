# Create agent-specific secret

1. Now create the agent-specific secret for the **IBM Db2 for z/OS Agent** by copying the following to a file called `db2-secret.yaml`:

    ```
    apiVersion: v1
    kind: Secret
    metadata:
      name: db2z-agent-secrets
      namespace: ""
    type: Opaque
    stringData:
      AGENT_AUTH_TOKEN: ""
      ENCRYPT_KEY: ""  
      DB2_AGENT_TOKEN: "IWRiMmFnZW50QA=="  
      LANGFUSE_SECRET_KEY: ""
      LANGFUSE_PUBLIC_KEY: ""
      ZOWE_ENABLED: "false"
    ```

1. Modify the following variables:
   
    - Set `metadata.namespace` to `wxa4z-agents`
  
    - Set `AGENT_AUTH_TOKEN` to any string of your choice for registration with WxO. 

    - Generate and set the `ENCRYPT_KEY` variable by following the <a href="https://github.com/IBM/z-ai-agents/tree/main/db2z-agent#generating-an-encrypt-key-with-python" target="_blank">steps documented here</a> to generate your encrypt key.


2. Once done, apply the secret by running:


    `oc apply -f db2-secret.yaml`

3. If not already created, you must create the `tz-pull-secret` secret in the `wxa4z-agents` namespace to deploy this agent. 
   
    Retrieve the <a href="https://ibm.box.com/s/7sm5v6nfzrm7r0vz64zyb81cmgx1x40e" target="_blank">entitlement key here</a>.

    Then run the following command, replacing `<entitlement-key>` with the value you copied:

    ```
    oc -n wxa4z-agents create secret docker-registry tz-pull-secret --docker-server=us.icr.io --docker-username=iamapikey --docker-password=<entitlement-key>
    ```
