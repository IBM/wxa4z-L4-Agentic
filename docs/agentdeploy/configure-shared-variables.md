# Configuring Shared (Global) Agent variables

Within your `values.yaml` file of the ***wxa4z-agent-suite*** folder, the first section of the file references `global` variables that get set first and are used by each of the agents.

After the global variables there are sections for each of the agents with agent-specific variables that must be set. In this section you will configure the global variables section of your `values.yaml` file.

**ACTION:** Within your VS Code window, click on the `values.yaml` file to open up the contents within VS Code.

**IMAGE**

**This is the file that you will be modifying in the following sections to prepare for your agents’ deployment. Ensure that you have the contents of this file opened within your VS Code window.**


### Configuring the `ORCHESTRATE_ENV_TYPE` global variable

At the very top of your `values.yaml` file, under global , there is a `secrets.data` section. You should see the `ORCHESTRATE_ENV_TYPE` variable:

```
secrets:
  name: wxa4z-watsonx-credentials 
  data:
    ORCHESTRATE_ENV_TYPE:
    ...
```

This is the instance type of your watsonx Orchestrate environment. Set the value to `ibm_iam` (for IBM Cloud). It should look like the following:

```
secrets:
  name: wxa4z-watsonx-credentials 
  data:
    ORCHESTRATE_ENV_TYPE: ibm_iam
    ...
```

### Configuring the `WATSONX_API_KEY` global variable

Below the previous variable (also under `secrets.data`) there is a global variable labeled `WATSONX_API_KEY`.

`WATSONX_API_KEY: “”`

Within the double-quotes, copy and paste your unique **API key** that you generated in the IBM Cloud console and recorded during Section ***[Generate IBM Cloud API key](../watsonx-ai/api-key.md)***.

### Configuring the `ORCHESTRATE_ENV_URL` global variable

Next you will see the `ORCHESTRATE_ENV_URL` variable under `secrets.data`. Within the double-quotes, copy and paste the value of your unique URL which you recorded in Section ***[Retrieve watsonx Orchestrate Service Instance URL](../watsonx-ai/service-instance-url.md)***.


### Configuring the `WATSONX_DEPLOYMENT_SPACE_ID` global variable

For the `WATSONX_DEPLOYMENT_SPACE_ID` global variable,copy and paste your unique Deployment Space ID within the double-quotes, which you recorded in Section ***[Create Deployment Space](../watsonx-ai/deployment-space.md)***.

### Configuring the `WATSONX_ML_URL` global variable

For the `WATSONX_ML_URL` global variable, copy and paste the value for your environment which you recorded in Section ***[Locate your WML Base URL](../watsonx-ai/wml-base-url.md)***.

### Configuring the `WATSONX_PROJECT_ID` global variable

Finally, for the `WATSONX_PROJECT_ID` global variable,copy and paste your unique Project ID that you recorded in Section ***[Create watsonx.ai Project](../watsonx-ai/project.md)***.


### Setting your registry entitlement key for wxa4z (for foundational agents)

After setting the above global variables within the `secrets.data` section of the `values.yaml` file, the last global secret to set is the registry image pull secret that will be used for pulling the images for the foundational agents. It should look like this by default under the `global` variables section:

```
registry:
    name: wxa4z-image-pull-secret 
    createSecret: true
    server: cp.icr.io
    username: cp 
    entitlementKey: “”
```

For the `entitlementKey` parameter, copy and paste the entitlement key you used in Section ***[Install the watsonx Assistant for Z Operator](../zAssistantDeploy/install-wxa4z-operator.md)***.

!!! Warning "If you forget your entitlement key"

    In the case that you don't remember the entitlement key you used and you need to generate a new one, follow these steps:

    1. Access the entitlement keys page [here](https://myibm.ibm.com/products-services/containerlibrary).
   
    2. Locate your existing entitlement key and click **copy**.


### Set `caTrustSync.enabled` to `false`



### Disable foundational agents not in scope


