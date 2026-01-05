# Enabling Db2 for z/OS Agent images

- As the **Db2 for z/OS Agent** is a **Prebuilt product agent**, versus the Foundational Agents previously configured, this agent requires additional setup which is detailed here: https://github.com/IBM/z-ai-agents/tree/main?tab=readme-ov-file#configuration-for-prebuilt-ibm-z-product-agents
  

- Typically, an entitlement key is requried to download the Db2 for z/OS Agent container images from the IBM Container Registry, and is available at no charge to licensed users of Db2 13. 

- For the purposes of setting up demos and the pilot environment, these images are made available internally in a private ICR that you can configure to pull the agent images from. This setup is detailed below. 

- **NOTE**: the entitlement key shown below is for ***INTERNAL USE ONLY**. For Business Partners, please contact your IBM rep. 

1. Within your `values.yaml` file, locate the section for the **Db2 for z/OS Agent** as shown below:

    ```
    # ---------------------------------------------------------------------------- #
    # Product: db2z-agent
    # ---------------------------------------------------------------------------- #

    db2z-agent:
      enabled: false
      acceptLicense: false # Must be true to install. Confirm Db2 Z agent license. https://www.ibm.com/support/customer/csol/terms/?id=L-RKLK-NBNFJL
      image:
        # additional agent-specific config....
    ```

2. Set `enabled: true` and `acceptLicense: true` to proceed with installation. Setting `acceptLicense: true` indicates consent to the license terms. 

3. Below those two variables you should then see the `image` and `mcpImage` blocks as shown below:
   
    ```
    enabled: true
    acceptLicense: true # Must be true to install. Confirm Db2 Z agent license. https://www.ibm.com/support/customer/csol/terms/?id=L-RKLK-NBNFJL
    image:
      repository: icr.io/ibm-db2z-ai/db2z-agent
      tag: latest@sha256:f2f080c4a3ab899ad6bb124d20197b663a2504347eabec7ab74efb20cad0dfa6
    mcpImage:
      repository: icr.io/ibm-db2z-ai/db2z-mcp-server
      tag: latest@sha256:04171657896a839504ccbae8197f1934fd81926d5467295b7318f133c15465ee
    ```

    As you will be pulling the agent images from an internal repo, you will next modify the `image` and `mcpImage` variables.

4. Set these variables to the following values as shown below:
   
    ```
    image:
      repository: us.icr.io/agents-txc/db2z-agent
      tag: v3.1.0-ga
    mcpImage:
      repository: us.icr.io/agents-txc/db2z-mcp-server
      tag: v3.1.0-ga
    ```

5. Underneath that section, you will see a `registry` variable block which looks like the following:
   
    ```
    registry:
      name: db2-image-pull-secret # Dedicated pull secret for this agent.
      server: icr.io
      username: iamapikey
      entitlementKey: ""
    ```

    Set the value of the `server` variable to `us.icr.io`:

    ```
    registry:
      name: db2-image-pull-secret # Dedicated pull secret for this agent.
      server: us.icr.io
      username: iamapikey
      entitlementKey: ""
    ```

    Then for the `entitlementKey` variable, set the value (in double-quotes) to the secret entitlement key that can be retrieved from <a href="https://ibm.box.com/s/oervr24pkj58xi1wgboumi1gbbm0vuai" target="_blank">here</a> (internal only).




