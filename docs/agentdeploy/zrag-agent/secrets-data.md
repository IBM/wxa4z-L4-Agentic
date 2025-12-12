# Configuring the `secrets.data` variables

Scrolling down further in the **zRAG Agent** section of your `values.yaml` file, you will see a **`secrets.data`** section with additional variables you must configure. It will look like what’s shown below:

```
secrets:
  data:
    CPD_USERNAME: ""
    WATSONX_API_KEY: ""
    WATSONX_PASSWORD: ""
```

As this is using a watsonx SaaS deployment, all that's needed is to populate the value of `WATSONX_API_KEY` to the Cloud API key you generated in ***Section [Generate IBM Cloud API key](../../watsonx-ai/api-key.md)***.

**Populate the value of `WATSONX_API_KEY` with your IBM Cloud API Key.**

Leave all other values empty. 