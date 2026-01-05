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

    a. Retrieve the `ZOSMF_ENDPOINT` variable you set when configuring the **Z Upgrade Agent** <a href="https://ibm.github.io/wxa4z-L4-Agentic/agentdeploy/upgrade-agent/secrets-data/#set-your-zosmf_endpoint-variable" target="_blank">here</a>.

    The result should look something like: `https://itzvsi-zos-ebds04j.vsi.techzone.ibm.com:10443/zosmf`

    b. Within that string, replace all the characters following the `:` with `5443`.

    In the above example, the result would be: `https://itzvsi-zos-ebds04j.vsi.techzone.ibm.com:5443`

    c. Set the final result to the `SERVICE_ENDPOINT` variable referenced above in your `values.yaml` file. 

3. Set the `WATSONX_MODEL_ID` variable to `meta-llama/llama-3-3-70b-instruct` as this is a cloud-based deployment. 

The final result should look similar to the following: 

```
env:
  DEPLOYMENT_TYPE: "cloud"           
  SERVICE_ENDPOINT: "https://itzvsi-zos-ebds04j.vsi.techzone.ibm.com:5443"
  WATSONX_MODEL_ID: "meta-llama/llama-3-3-70b-instruct"
```
