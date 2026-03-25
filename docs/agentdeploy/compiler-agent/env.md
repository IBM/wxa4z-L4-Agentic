# Configuring the `env` variables

Within your `values.yaml` file, locate the `env` section for the **compiler-fix-finder** Agent as shown below:

```
env:
  WATSONX_MODEL_ID: "ibm/granite-3-3-8b-instruct"
```
Enter the **MODEL ID** corresponding to the LLM for your use case. The suggestion for TechZone cloud-based environments is to use the `meta-llama/llama-3-3-70b-instruct` model. However, if you've completed the [optional setup](../../watsonx-ai/config-granite.md) for configuring the Model Gateway for Granite, you can leave the default `ibm/granite-3-3-8b-instruct` MODEL_ID. 

Then ensure you save the file.