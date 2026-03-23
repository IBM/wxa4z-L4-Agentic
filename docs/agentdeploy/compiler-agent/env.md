# Configuring the `env` variables

Within your `values.yaml` file, locate the `env` section for the **compiler-fix-finder** Agent as shown below:

```
env:
  WATSONX_MODEL_ID: "ibm/granite-3-3-8b-instruct"
```

Enter the **MODEL ID** corresponding to the LLM of your use case. If you've completed the Granite setup in Section...then you can use the `ibm/granite-3-3-8b-instruct` MODEL_ID. If not, then use the `meta-llama/llama-3-3-70b-instruct` MODEL_ID.
