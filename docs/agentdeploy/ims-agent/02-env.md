# Configuring the `env` variables

    DEPLOYMENT_TYPE: "cloud"              
    ZOSMF_CONSOLE_NAME: "iserVS01"
    IMS_SUBSYSTEM_ID: "IVP1"
    IMS_CONNECT_JOBNAME: "IMS15HWS"
    APPL_ID: "IZUDFLT"
    WATSONX_MODEL_ID: "meta-llama/llama-3-3-70b-instruct"

You will now configure these `env` variables, using the defaults according to the zD&T Image configuration.

The below table describes each of the variables in the `env` variables section.

**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**DEPLOYMENT_TYPE** | Type of deployment (options include 'on-prem' and 'cloud') | "cloud"
**ZOSMF_CONSOLE_NAME** | Specifies the name of the z/OS system console that will be used by z/OSMF (z/OS Management Facility) to interact with IMS. | "iserVS01"
**IMS_SUBSYSTEM_ID** | IMS subsystem instance ID. | "IVP1"
**IMS_CONNECT_JOBNAME** | Specifies the job name of IMS Connect. | "IMS15HWS"
**APPL_ID** | ZOSMF Application ID, typically defaults to IZUDFLT. | "IZUDFLT"
**WATSONX_MODEL_ID** | LLM Model used by the agent. For example, "meta-llama/llama-3-3-70b-instruct" | "meta-llama/llama-3-3-70b-instruct"
----
