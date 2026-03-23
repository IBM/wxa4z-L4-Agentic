# Enabling the Compiler Fix Finder Agent images

The **IBM Z Compilers Fix Finder Agent** is a **Product-specific agent** which requires an entitlement key to download the agent images. 

For the purpose of setting up demos and the pilot environment, these images are being made available internally in a private ICR that you can configure to pull the agent images from. 

**NOTE:** the entitlemnt key shown below is for **INTERNAL USE ONLY**. 
For Business Partners, please contact your IBM rep. 

1. Within your `values.yaml` file, locate the section for the **compiler-fix-finder-agent** as shown below:

    ```
    # ---------------------------------------------------------------------------- #
    # Product: compiler-fix-finder-agent
    # ---------------------------------------------------------------------------- #

    compiler-fix-finder-agent:
      enabled: false
      acceptLicense: false # Must be true to install. Reference Compiler Fix Finder Agent license: https://www.ibm.com/support/customer/csol/terms/?id=L-UYYT-82EFMW
      # additional agent-specific config....
    ```

2. Set `enabled: true` and `acceptLicense: true` to proceed with installation. Setting `acceptLicense: true` indicates consent to the license terms. 


3. Underneath that section, you will see a `registry` variable block which looks like the following:
   
    ```
    registry:
      name: z-compiler-fix-finder-image-pull-secret
      server: icr.io
      username: iamapikey
      entitlementKey: ""

    ```

    Set the value of the `server` variable to `us.icr.io`:

    ```
    registry:
      name: z-compiler-fix-finder-image-pull-secret
      server: us.icr.io
      username: iamapikey
      entitlementKey: ""
    ```

    Then for the `entitlementKey` variable, set the value (in double-quotes) to the secret entitlement key that can be retrieved from <a href="https://ibm.box.com/s/oervr24pkj58xi1wgboumi1gbbm0vuai" target="_blank">here</a> (internal only).


4. Below that, you should see an `image` block as shown below:
   
    ```
    image:
      repository: icr.io/zoscp/ibm-z-compilers-fix-finder-agent
      tag: 1.2.0@sha256:11bc5c3a376fe759dacb48bcef47c93d2e8a0469e58811f1737d3fb62eb56368
    ```

    As you will be pulling the agent image from an internal registry, modify these variables to the following values as shown below:
  
    ```
    image:
      repository: us.icr.io/agents-txc/ibm-z-compilers-fix-finder-agent
      tag: 1.2.0
    ```


