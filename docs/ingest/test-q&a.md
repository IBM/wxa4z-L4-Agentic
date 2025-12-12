# Test zRAG Agent with newly ingested documents

Now that you’ve successfully ingested the sample customer documents, you’ll be able to test the agent's ability to answer company-specific questions related to the internal documents. 

1. Navigate back to the **zRAG Agent Editor** page by following the steps ***[here](../demo-scenarios/access-agents.md)*** and clicking on the **zRAG Agent** tile. 


2. ***Enter the following prompts*** to your agent that are specifically referencing the sampled documentation provided. For each of the provided prompts, an example output is provided which may be different from your agent's response. For each response, feel free to view the referenced citation to identify where the answer was taken from.

    **PROMPT:**

    ```
    The customer application is failing with ERR-CBL-001, what does this internal error mean?
    ```

    ***Example Output:***

    ![](_attachments/agent-ingest1.png)


    **PROMPT:**

    ```
    What specific syntax changes do I need to make in COBOL to call Java using the internal framework?
    ```

    ***Example Output:***

    ![](_attachments/agent-ingest2.png)

    **PROMPT:**

    ```
    What is the internal git lab link to execute the Java on z/OS pipeline?
    ```

    ***Example Output:***

    ![](_attachments/agent-ingest3.png)

    
    **PROMPT:**

    ```
    Are there any production incidents that were resolved in relation to Data corruption in the production database? If yes who can I collaborate with to resolve a similar issue today and what are their names?
    ```

    ***Example Output:***

    ![](_attachments/agent-ingest4.png)




