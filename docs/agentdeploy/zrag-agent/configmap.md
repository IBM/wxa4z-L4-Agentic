# Configuring the `configmap` variables

Within your `values.yaml` file, locate the section for the **zRAG Agent** as shown below:

```
# ---------------------------------------------------------------------------- #
# Foundational: zrag-agent
# ---------------------------------------------------------------------------- #
zrag-agent:
  enabled: true
  image:
    # additional agent-specific config....
```

Within this agent’s section of `values.yaml` scroll down to the **`configmap`** variable section which by default should look like what’s shown below:

```
configmap:
  MODEL_ID: "meta-llama/llama-3-3-70b-instruct"
  ZRAG_RETRIEVER_URL: "https://wxa4z-opensearch-wrapper.wxa4z-zad.svc.cluster.local:8080"
```

The `MODEL_ID` variable maps to the LLM model used by the zRAG MCP server for answer generation. For the TechZone environment, the `MODEL_ID` variable can be set to one of the following:

- `meta-llama/llama-3-3-70b-instruct`
- `ibm/granite-4-h-small`
  
!!! Warning "Withdrawal of `granite-3-3-8b-instruct`..."

    The watsonx Assistant for Z product officially supports `llama-3-3-70b-instruct` for x86 and the `granite-3-3-8b-instruct` model when deployed on s390x. Due the withdrawal of the `granite-3-3-8b-instruct` model from watsonx.ai on IBM Cloud, the recommended substitute is the `granite-4-h-small` model. You should only use this model for use cases requiring multi-lingual support for languages not supported by the llama model (i.e. Japanese and Chinese). Otherwise, the recommended model is `llama-3-3-70b-instruct`. Use at your own discretion. 


Keep the default value for the `ZRAG_RETRIEVER_URL` as this is the URL endpoint for the OpenSearch wrapper service. 