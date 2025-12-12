# Configuring the `env` variables

Within your `values.yaml` file, locate the section for the **db2z-agent** as shown below:

```
# ---------------------------------------------------------------------------- #
# Product: db2z-agent
# ---------------------------------------------------------------------------- #
db2z-agent:
  enabled: true
  acceptLicense: true
  image:
    # additional agent-specific config....
```

Within this agent’s section of `values.yaml` scroll down to the **`env`** variable section which by default should look like what’s shown below:

```
env:
  DEPLOYMENT_TYPE: ""
  SERVICE_ENDPOINT: ""
  WATSONX_MODEL_ID: ""
```

You will now configure these `env` variables, using some defaults, as well as your environment-specific values.

The below table describes each of the variables in the `env` variables section. The rows with default values can be set to what's shown in the `Default value to set` column. The rows without default values are unqiue to your environment and will require you to set that value using the instructions below in this section. 

**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**DEPLOYMENT_TYPE** | Type of deployment (options include 'on-prem' and 'cloud') | "cloud"
**SERVICE_ENDPOINT** | URL of the service endpoint to generate passticket and user to establish connection to Db2. | -------
**WATSONX_MODEL_ID** | LLM Model used by the agent. For example, "meta-llama/llama-3-3-70b-instruct" or "ibm/granite-3-3-8b-instruct" | meta-llama/llama-3-3-70b-instruct


1. Firstly, ensure the `enabled` and `acceptLicense` parameters are both set to `true` in the beginning of the agent section. 
   
2. Set the default variable values for the rows above in your `values.yaml` file:

    * `DEPLOYMENT_TYPE: "cloud"`
    * `WATSONX_MODEL_ID: "meta-llama/llama-3-3-70b-instruct"`


3. Set the `SERVICE_ENDPOINT` variable to.....
   
    !!! Warning "Bypassing authorization service"

        Typically, the `SERVICE_ENDPOINT` variable is set to the endpoint where you have passtickets configured.....
   