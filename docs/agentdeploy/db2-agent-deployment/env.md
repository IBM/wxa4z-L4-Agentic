# Configuring the `env` variables

Within your `values.yaml` file, locate the `env` section for the **Db2 for z/OS** Agent as shown below:

```
env:
  DEPLOYMENT_TYPE: "cloud"
  SERVICE_ENDPOINT: ""
  WATSONX_MODEL_ID: "ibm/granite-3-3-8b-instruct"
```

1. Keep the `DEPLOYMENT_TYPE` variable set to `cloud`

2. While the `SERVICE_ENDPOINT` variable would point to the URL endpoint on z/OS to generate user passtickets, that setup isn't detailed here and will be bypassed for the purpose of demos. 
   
    Set `SERVICE_ENDPOINT` by following the below steps:

    a. Retrieve the **public ip** address of your zD&T environment (follow [this section](../../techzone/zdt.md#accessing-the-environment) for steps to retrieve it).

    b. Then, replace `<public-ip>` in the following string with the value of your environment's value:

    `https://<public-ip>:5443`

    c. Set the final result to the `SERVICE_ENDPOINT` variable referenced above in your `values.yaml` file. 

3. Set the `WATSONX_MODEL_ID` variable to the LLM for your use case. The suggestion for TechZone cloud-based environments is to use the `meta-llama/llama-3-3-70b-instruct` model. However, if you've completed the [optional setup](../../watsonx-ai/config-granite.md) for configuring the Model Gateway for Granite, you can leave the default `ibm/granite-3-3-8b-instruct` MODEL_ID. 

