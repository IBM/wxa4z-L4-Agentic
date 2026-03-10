# Additional setup for zRAG Agent

The final setup that's needed to successfully bootstrap the zRAG Agent with the provided MCP tools is to make some modifications to your toolkit name. This is a workaround for a known bug within watsonx Orchestrate on IBM Cloud, in which MCP toolkit names must be unique across tenants. **If you don't follow the steps below and leave the default toolkit name, then the bootstrap process will fail for your zRAG Agent.**

All modifications thus far have been in the `wxa4z-agent-suite/values.yaml` file of your `Z-AI-AGENTS` folder structure. 

For the below steps, you will need to navigate to the `agent-helm-charts/zrag-agent/config/` folder which contains 3 files:

  - zrag_agent_bootstrap_config.yaml
  - zrag_agent_granite.yaml
  - zrag_agent.yaml

The folder structure looks like the following:

```
wxa4z-agent-suite/
agent-helm-charts/
    ├─ automation-insights-agent/ 
    ├─ cics-agent/ 
    ├─ ...
    ├─ zrag-agent/
        ├─ config/ 
 -------->  ├─ zrag_agent_bootstrap_config.yaml <---
 -------->  ├─ zrag_agent_granite.yaml          <---
 -------->  ├─ zrag_agent.yaml                  <---
        ├─ templates/
        ├─ ...
```

1. Once navigated to the `agent-helm-charts/zrag-agent/config/` folder, open the `zrag_agent_bootstrap_config.yaml` file. Towards the bottom of the file you should see a section for **Toolkits** as shown below:
   
    ```
    toolkits:
    - name: zrag-mcp-toolkit<REPLACE>
      kind: mcp
      import_method: cli
      description: "zRAG document retrieval and RAG toolkit with watsonx.ai integration for mainframe and enterprise systems"
      #command: "uvx mcp-proxy {route_url}/sse"
      url: "{route_url}"
      route_name: ${ZRAG_ROUTE_NAME}
      route_namespace: ${ZRAG_ROUTE_NAMESPACE}
      route_path: "/sse"
      transport: "sse"
      tools: "*"
      app_id: zrag-mcp-connection
      replace: true
    ```

2. Within the above text, modify the `name` parameter, replacing `<REPLACE>` with a unique string of your choice (must be unique).
   
    This can be anything and won't affect the agent functionality or appearance. For example, use your name followed by the date:

    `jsmith0310`

    In the above example, this section of the `zrag_agent_bootstrap_config.yaml` file would look something like:

    ```
    toolkits:
    - name: zrag-mcp-toolkit-jsmith0310
      kind: mcp
      import_method: cli
      description: "zRAG document retrieval and RAG toolkit with watsonx.ai integration for mainframe and enterprise systems"
      #command: "uvx mcp-proxy {route_url}/sse"
      url: "{route_url}"
      route_name: ${ZRAG_ROUTE_NAME}
      route_namespace: ${ZRAG_ROUTE_NAMESPACE}
      route_path: "/sse"
      transport: "sse"
      tools: "*"
      app_id: zrag-mcp-connection
      replace: true
    ```

    !!! Warning "Record this string..."

        The string you used in the previous step must be randomized and unique. Record this string as you must use the exact same string for the other files referenced below. 


3. Once modified, make sure to save the file. 


4. Next, open up the `zrag_agent_granite.yaml` file within the same folder. In the `tools` section of the agent definition, you should see the following:
   
    ```
    tools:
       - zrag-mcp-toolkit<REPLACE>:zrag_retriever
       - zrag-mcp-toolkit<REPLACE>:health_check
    ```

    Just like before, modify `<REPLACE>` on both lines with the same string used in the previous file. For example:

    ```
    tools:
       - zrag-mcp-toolkit-jsmith0310:zrag_retriever
       - zrag-mcp-toolkit-jsmith0310:health_check
    ```

    Then save the file. 

5. Lastly, open up the `zrag_agent.yaml` file within the same folder. Repeat the above step, replacing `<REPLACE>` with the same string, then save the file. 

6. Once done, you can navigate back to the `wxa4z-agent-suite/values.yaml` file to continue in the following sections. 