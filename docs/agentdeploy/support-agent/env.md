# Configuring the `env` variables

Within your `values.yaml` file, locate the section for the **IBM Z Support Agent** as shown below:

```
# ---------------------------------------------------------------------------- #
# Foundational: support-agent
# ---------------------------------------------------------------------------- #
support-agent:
  enabled: true
  image:
    # additional agent-specific config....
```

Within this agent’s section of `values.yaml` scroll down to the **`env`** variable section which by default should look like what’s shown below:

```
env:
  DEPLOYMENT_TYPE:
  TAKE_DUMP_JOB_TEMPLATE: ""
  SEND_DUMP_JOB_TEMPLATE: ""
  WATSONX_MODEL_ID: "ibm/granite-3-3-8b-instruct"
```

The below table describes each of the variables in the `env` variables section.

**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**DEPLOYMENT_TYPE** | Type of deployment (options include 'on-prem' and 'cloud') | "cloud"
**TAKE_DUMP_JOB_TEMPLATE** | Name of AAP Template used for gathering/collecting dumps | "Collect dump"
**SEND_DUMP_JOB_TEMPLATE** | Name of AAP Template used for sending/transferring dumps to IBM Support | "Send dump"
**WATSONX_MODEL_ID** | LLM Model used by the agent. For example, "meta-llama/llama-3-3-70b-instruct" | "meta-llama/llama-3-3-70b-instruct"
----


***NOTE:*** because you are using a pre-configured instance of AAP/Wazi aaS, the required template names are hard-coded. 

**Set the above default values** in your `values.yaml` file under the `env` variables section. *The result should look like the following:*

```
env:
  DEPLOYMENT_TYPE: "cloud"
  TAKE_DUMP_JOB_TEMPLATE: "Collect dump"
  SEND_DUMP_JOB_TEMPLATE: "Send dump"
  WATSONX_MODEL_ID: "meta-llama/llama-3-70b-instruct"
```