# Custom Search Configurations for zRAG Retriever

Once deployed, the zRAG Agent may require additional fine-tuning depending on the use case and the topic of questions being asked. 

When a user queries the zRAG Agent with a question, the following flow is executed:

1. User issues query to zRAG Agent chat interface in Orchestrate
2. Orchestrate agent invokes the **zrag_retriever** tool with the exact query.
3. **zrag_retriever** executes document retrieval against OpenSearch knowledge base, leveraging the search configuration that is configured in the **zrag-mcp-connection** Orchestrate connection. 
4. Search is executed and the tool returns ranked document set with metadata
5. zRAG Orchestrate agent passes results to LLM for answer generation.
6. Final answer streams back to chat window with citations. 

## Modifying Search Configuration

In step 3 of the flow above, document retrieval is done leveraging the search configuration defined in the `zrag-mcp-connection` connection within watsonx Orchestrate. By default, the connection details are set during the zRAG Agent bootstrapping process. But depending on use case and for fine-tuning purposes, these connection search parameters should be modified as discussed below. 

This section will outline the most relevant scenarios for modifying the search configuration. For full details, refer to the **<a href="https://github.com/IBM/z-ai-agents/tree/main/agent-helm-charts/zrag-agent#custom-search-configurations-for-zrag-retriever" target="_blank">documentation here</a>**.

There are two methods of modifying the `zrag-mcp-connection` search configuration:

### Method 1: Using watsonx Orchestrate UI

The first method is by using the watsonx Orchestrate web interface to set connection credentials directly as key-value pairs. To do this, follow the below steps:

1. Log into your watsonx Orchestrate environment UI by following the steps ***[here](../../watsonx-ai/service-instance-url.md)***.

2. Once logged in, go to the **Connections** view by clicking on the hamburger icon in top-left, then selecting **Manage --> Connections**. 

    ![](_attachments/search1.png)


3. There you should see your `zrag-mcp-connection` pre-defined. 
   
    Click on the **Credentials** tab. 

    ![](_attachments/search2.png)

4. In the **Credentials** view, you'll see a tab for both the **Draft** and **Live** environment. Ensure that any changes you test/verify for the **Draft** environment also gets made to the **Live** environment in order to take affect for end-users. 
   
    Next to the `zrag-mcp-connection`, click on the ellipses then select **Edit**. 

    ![](_attachments/search3.png)

5. Modify any of the default key-pair values by clicking on the pencil icon based on requirement. 
   
    ![](_attachments/search4.png)

    Or alternatively, add a new key-pair value for a search parameter that isn't assigned by default (i.e. `ZRAG_TOPICS_ENABLE`, `ZRAG_TOPICS_DISABLE`, `ZRAG_METADATA_PRODUCT_WEIGHT`, etc.). This can be done by scrolling to the bottom and selecting **Add key value pair +**. 

    ![](_attachments/search5.png)

6. Once done, save the changes. 
   
    For a full list of available search parameters, refer to the **<a href="https://github.com/IBM/z-ai-agents/tree/main/agent-helm-charts/zrag-agent#custom-search-configurations-for-zrag-retriever" target="_blank">documentation here</a>**.


### Method 2: Using Orchestrate ADK CLI

Alternatively, you can modify the connection credentials programatically using the ADK CLI. For steps on doing this, reference the **<a href="https://github.com/IBM/z-ai-agents/tree/main/agent-helm-charts/zrag-agent#method-2-using-orchestrate-adk-cli" target="_blank">steps here</a>**.


# Scenarios

The below scenarios outline the most common search configuration updates you may need to make with examples. 

## 1.) Disabling certain topics

One of the most common scenarios is disabling certain topics that are not relevant to the customer or the use case. As an example, if when using the default zRAG search settings, references to z/VM or z/TPF are unintentionally surfacing in generated responses and citations, you may need to explicitly disable these topics from being referenced. 

This can be done using the `ZRAG_TOPICS_DISABLE` search parameter. By default, this parameter is not included in the connection credentials and will need to be added if you intend on using it. 

To use this parameter to disable the z/VM or z/TPF topics, you can first modify the connection credentials for the draft environment:

1. Follow the steps in **[Method 1: Using watsonx Orchestrate UI](./zrag-config.md#method-1-using-watsonx-orchestrate-ui)** to edit the **Draft** connection credentials.
   

2. At the bottom of the **Edit credential** view, click **Add key value pair +** as this parameter isn't included by default. 
   
    ![](_attachments/search6.png)

3. In the **Key** field, enter `ZRAG_TOPICS_DISABLE`. In the **Value** field, enter `z/vm,z/tpf` for this example. 
   
    ![](_attachments/search7.png)

4. Then click **Save**. 

NOTE: because you only modified the connection credentials for the **Draft** environment, the search configuration will only be passed to the retriever when prompting the agent in the **Draft/Editor** view. It won't take affect for end-users until you also modify the **Live** environment. 

### Testing the configuration







## 2.) Enabling only certain topics

Alternatively, if the use case is very tightly scoped on base z/OS functionality and ignoring other IBM tooling/middleware/products, you can scope the search to only the base z/OS documentation, forcing the retrieval to ignore all other topics. This can be done using the `ZRAG_TOPICS_ENABLE` search parameter.

***NOTE: only the ENABLE/DISABLE parameters can be used at once***....


To do this:

1. First delete the ZRAG_TOPICS_DISABLE FILTER. 



## 3.) Modifying doc weights



## 4.) Modifying specific doc indices to search


