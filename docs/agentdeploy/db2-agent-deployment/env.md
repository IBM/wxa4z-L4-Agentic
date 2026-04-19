# Configuring the `env` variables

Within your `values.yaml` file, locate the `env` section for the **Db2 for z/OS** Agent as shown below:

```
env:
  DEPLOYMENT_TYPE: "cloud"
  SERVICE_ENDPOINT: ""
  WATSONX_MODEL_ID: "meta-llama/llama-3-3-70b-instruct"
```

1. Keep the `DEPLOYMENT_TYPE` variable set to `cloud` if not already.

2. While the `SERVICE_ENDPOINT` variable would point to the URL endpoint for the Token Exchange Service, that setup isn't detailed here and will be bypassed for the purpose of demos. 
   
    Set `SERVICE_ENDPOINT` by following the below steps:

    a. Retrieve the **public ip** address of your zD&T environment (follow [this section](../../techzone/zdt.md#accessing-the-environment) for steps to retrieve it).

    b. Then, replace `<public-ip>` in the following string with the value of your environment's value:

    `https://<public-ip>:5443`

    c. Set the final result to the `SERVICE_ENDPOINT` variable referenced above in your `values.yaml` file. 

