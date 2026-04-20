# Enabling IMS Agent images

The **IBM IMS Agents** is a **Prebuilt product agent**, versus the Foundational Agents previously configured, and requires additional setup which is detailed **<a href="https://github.com/IBM/z-ai-agents/tree/main?tab=readme-ov-file#configuration-for-prebuilt-ibm-z-product-agents" target="_blank">here</a>**.

*For the purposes of setting up demos and the pilot environment, these images are made available internally in a private ICR that you can configure to pull the agent images from. This setup is detailed below.*

!!! Warning "Entitlement for clients..."

    An entitlement key is required to download the Db2 for z/OS Agent container images from the IBM Container Registry, and is available at no charge to licensed users of Db2 13. **The steps below are for internal use only.**

    For **Business Partners**, please contact your IBM rep. 


1. Within your `values.yaml` file, locate the section for the **IBM IMS Agents** as shown below:

    ```
    # ---------------------------------------------------------------------------- #
    # Product: ims-agent
    # ---------------------------------------------------------------------------- #

    ims-agent:
      enabled: false
      acceptLicense: false # Must be true to install. Confirm Db2 Z agent license. https://www.ibm.com/support/customer/csol/terms/?id=L-RKLK-NBNFJL
      image:
        # additional agent-specific config....
    ```

2. Set `enabled: true` and `acceptLicense: true` to proceed with installation. Setting `acceptLicense: true` indicates consent to the license terms. 

3. Below those two variables you should then see the `image` and `mcpImage` blocks as shown below:
   
    ```
    enabled: true
    acceptLicense: true
    image:
      repository: icr.io/ibm-ims-ai/ims-qa-agent
      tag: 1.0.2
    mcpImage:
      repository: icr.io/ibm-ims-ai/ims-mcp-agent
      tag: 1.0.2
    ```

    As you will be pulling the agent images from an internal container registry, you will next modify the `image` and `mcpImage` variables.

4. Set these variables to the following values as shown below:
   
    ```
    image:
      repository: us.icr.io/agents-txc/ims-qa-agent
      tag: 1.0.2
    mcpImage:
      repository: us.icr.io/agents-txc/ims-mcp-agent
      tag: 1.0.2
    ```


5. Underneath that section, you will see a `registry` variable block which looks like the following:
   
    ```
    registry:
      name: ims-image-pull-secret
      server: icr.io
      username: iamapikey
      entitlementKey: ""
    ```

    Set the value of the `server` variable to `us.icr.io`:

    ```
    registry:
      name: ims-image-pull-secret
      server: us.icr.io
      username: iamapikey
      entitlementKey: ""
    ```

    Then for the `entitlementKey` variable, set the value (in double-quotes) to the secret entitlement key that can be retrieved from <a href="https://ibm.box.com/s/oervr24pkj58xi1wgboumi1gbbm0vuai" target="_blank">here</a> (internal only).