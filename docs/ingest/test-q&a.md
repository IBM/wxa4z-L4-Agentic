# Test Assistant Q&A with newly ingested documents

Now that you’ve successfully ingested the sample customer documents, you’ll be able to test the assistant’s ability to answer company-specific questions related to the internal documents. First you will adjust your assistant’s conversational search settings to prioritize the ingested documents. 

Secondly, you will prompt the assistant with questions related to those documents to gauge performance.

### Adjust conversational search settings for ingested documentation

First, you will adjust the conversational search settings for your assistant in order to prioritize the ingested documents for Q&A.

1. Navigate back to the **watsonx Orchestrate UI**.

2. Go to the **Assistant Builder** view by clicking on **Build --> Assistant Builder**.
   
    **IMAGE**


3. In the left-side navigation, click on **Generative AI**.
   
    **IMAGE**

4. At the bottom of the screen, click on **View search integration**.
   
    **IMAGE**

5. Then click **Custom Service**. 
   
6. Scroll down to the **Metadata** field and modify it to prioritize your newly ingested documents.
   
    Currently, your **Metadata** field should look like what’s shown below:

    ```
    {"doc_weight":
    {"product_docs":0.5,
    "customer_docs":0.5},
    "ibm_indices":"*_ibm_docs_slate,*_ibm_redbooks_slate","standardize":true,
    "customer_indices":"customer_*"}
    ```

    Notice that `product_docs` and `customer_docs` are set equally (`0.5`). This is the default and causes the Assistant to prioritize the data search equally between the IBM documentation and the customer documents. 

    In this case, we want the Assistant to prioritize the newly ingested customer docs. To do this, **set** `product_docs` to `0.2` and set `customer_docs` to `0.8`. When done, your **Metadata** field should look like the following:

    ```
    {"doc_weight":
    {"product_docs":0.2,
    "customer_docs":0.8},
    "ibm_indices":"*_ibm_docs_slate,*_ibm_redbooks_slate","standardize":true,
    "customer_indices":"customer_*"}
    ```


7. Secondly, you have the ability to set the scope of customer documentation that gets searched when generating a response. By default, `customer_indices` is set to `customer_*`.
   
    What this means is that all ingested documents from all of your ingested sources will be searched. In the case where you want to narrow the scope of the ingested documents to a single source, this can be modified to point to that source.

    Recall the output of the `zassist list` command. For example:

    **IMAGE**

    In the example above, when running the command to ingest documents, the `<source name>` provided was `my_source`. ***Note***: your source name may be different. To check, issue the `zassist list` command on your command-line.

    In this case, we’ve only created one source. But in the case you have multiple sources, each with their own set of ingested documents, it would be possible to narrow the scope of documents available to the assistant by configuring the `customer_indices` parameter in the **Metadata** field.

    To do this, **modify** the `customer_indices` value by replacing `customer_*` with `customer_<your_source_name>`.

    Using the screenshot above as an example, the new **Metadata** field would look like the following:

    ```
    {"doc_weight":
    {"product_docs":0.2,
    "customer_docs":0.8},
    "ibm_indices":"*_ibm_docs_slate,*_ibm_redbooks_slate","standardize":true,
    "customer_indices":"customer_my_source"}
    ```

    **NOTE**: do not copy and paste exactly what's shown above. Make sure to use your unique source name. 


8. Lastly, for the purpose of testing Q&A for the ingested documents, set the **Contextual awareness** setting to **Single turn**. Then click **Save** and **Close**.

    **IMAGE**


### Test client-specific Q&A with ingested documents

Now that you’ve successfully ingested the sample customer documents and modified your conversational search settings, you’re ready to verify the assistant’s usage of the ingested documents.

1. Navigate back to the **Preview** page by hovering your cursor over the left-side navigation and clicking **Preview**. 

    **IMAGE**

2. ***Enter the following prompts*** to your assistant that are specifically referencing the sampled documentation provided. For each of the provided prompts, an example output is provided which may be different from your assistant’s response. For each response, feel free to view the referenced citation to identify where the answer was taken from.

    **PROMPT:**

    ```
    The customer application is failing with ERR-CBL-001, what does this internal error mean?
    ```

    ***Example Output:***

    **SCREENSHOT**


    ***Click the citations drop-down at the bottom of the response. Notice how your ingested documented is referenced. Feel free to click on the citation to check the reference.***

    **IMAGE**

    **PROMPT:**

    ```
    What specific syntax changes do I need to make in COBOL to call Java using the internal framework?
    ```

    ***Example Output:***

    **SCREENSHOT**

    **PROMPT:**

    ```
    What is the internal git lab link to execute the Java on z/OS pipeline?
    ```

    ***Example Output:***

    **SCREENSHOT**

    
    **PROMPT:**

    ```
    Are there any production incidents that were resolved in relation to Data corruption in the production database? If yes who can I collaborate with to resolve a similar issue today and what are their names?
    ```

    ***Example Output:***

    **SCREENSHOT**




