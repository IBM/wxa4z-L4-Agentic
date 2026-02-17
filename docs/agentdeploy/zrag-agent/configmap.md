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
  MODEL_ID: ""
  ZRAG_RETRIEVER_URL: "https://wxa4z-opensearch-wrapper.wxa4z-zad.svc.cluster.local:8080"
```

The `MODEL_ID` variable maps to the LLM model used by the zRAG MCP server for answer generation. 

**Modify this to `meta-llama/llama-3-3-70b-instruct`** as this is a cloud-based x86 deployment. 

***NOTE:*** if you want to enable the **granite-3-3-8b-instruct** LLM, ensure you completed the steps documented in Section ***[OPTIONAL: Configuring Model Gateway service for Granite LLM](../../watsonx-ai/config-granite.md)***.

Keep the default value for the `ZRAG_RETRIEVER_URL` as this is the URL endpoint for the OpenSearch wrapper service. 