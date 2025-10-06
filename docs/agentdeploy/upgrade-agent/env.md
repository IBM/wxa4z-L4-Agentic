# Configuring the `env` variables

Within your `values.yaml` file, locate the section for the **IBM Z Upgrade Agent** as shown below:

```
# ---------------------------------------------------------------------------- #
# Default: upgrade-agent
# ---------------------------------------------------------------------------- #
upgrade-agent:
  enabled: true
  image:
    # additional agent-specific config....
```

Within this agent’s section of `values.yaml` scroll down to the **`env`** variable section which by default should look like what’s shown below:

```
env:
  DEPLOYMENT_TYPE:
  WRAPPER_URL: ""
  HOST_NAME: ""
  PDS_NAME: ""
  INGESTION_URL: ""
```

You will now configure these `env` variables, using some defaults, as well as your environment-specific values.

The below table describes each of the variables in the `env` variables section. The rows with default values can be set to what's shown in the `Default value to set` column. The rows without default values are unqiue to your environment and will require you to set that value using the instructions below in this section. 

**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**DEPLOYMENT_TYPE** | Type of deployment (options include 'on-prem' and 'cloud') | "cloud"
**WRAPPER_URL** | Wrapper URL for OpenSearch deployment. | -------
**HOST_NAME** | Endpoint of the cluster in which the agent is deployed | -------
**PDS_NAME** | Name of PDS dataset to be used for storing REXX scripts | "IBMUSER.REXX"
**INGESTION_URL** | URL endpoint of the client ingestion service used for ingesting required agent documents | -------

1. Set the default variable values for the rows above in your `values.yaml` file:

    * `DEPLOYMENT_TYPE: "cloud"`
    * `PDS_NAME: "IBMUSER.REXX"`

2. Set the `WRAPPER_URL` variable to the URL endpoint of the your OpenSearch wrapper deployment you recorded in Section ***[Verify deployment and acquire OpenSearch connection details](../../zAssistantDeploy/verify-deployment.md)***.
  

    !!! Tip "This can also be found by...."
    
        This can also be found by logging into the OCP Web console, navigating to **Networking --> Routes**, and then copying the route location of the `wxa4z-opensearch-wrapper` route (appending `/v1/query` to it).

        An example URL looks like the following:
        `https://wxa4z-opensearch-wrapper-wxa4z- zad.apps.68b1c328e1b1c3e282ce4781.eu1.techzone.ibm.com/v1/query`