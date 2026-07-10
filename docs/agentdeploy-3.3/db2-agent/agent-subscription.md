# Subscribe agent to tenant

Finally, subscribe the agent to automate the bootstrapping of the **OMEGAMON Insights Agent** to your watsonx Orchestrate environment. 

1. Before creating the **Agent Subscription**, first modify the **configMap** for the agent bootstrapper, called `omegamon-insights-agent-bootstrap-config`.
   
    a. Navigate to the `ConfigMaps` section in your `wxa4z-agents` namespace:

    ![](_attachments/sub1.png)

    b. Click on the `omegamon-insights-agent-bootstrap-config` resource

    ![](_attachments/sub2.png)

    c. Click on **Edit ConfigMap**. 

    ![](_attachments/sub3.png)

    d. In the Editor view, find the first `omegamon_insights_agent.yaml` key. You will modify the `llm` section.

    ![](_attachments/sub4.png)

    e. If using the `meta-llama/llama-3-3-70b-instruct` **MODEL_ID**, modify the `llm` section by removing the `virtual-model` string. The result should be:

    ```
    llm: watsonx/meta-llama/llama-3-3-70b-instruct
    ```

    f. Then click **Save**. 

    ![](_attachments/sub5.png)

    The purpose of this is to properly select the LLM used by the Orchestrator agent when it gets bootstrapped. For watsonx Orchestrate SaaS, the `llm` value should be `watsonx/meta-llama/llama-3-3-70b-instruct` or `groq/openai/gpt-oss-120b` as 2 examples. 


2. Once done, copy and paste the following into a file called `omegamon-subscribe.yaml`:

    ```
    apiVersion: wxa4z.watsonx.ibm.com/v1alpha1
    kind: AgentSubscription
    metadata:
      name: omegamon-agent-z-subscription
      namespace: wxa4z-agents
    spec:
      agent:
        agent_id: wxa4z:omegamon-agent-z:agent
        name: omegamon-insights-agent
        type: external
      tenant_id: ''
      wxa4z-core-services-namespace: wxa4z-zad
    ```

3. Set `tenant_id` to your environment's tenant id that you recorded [here](../setup.md#record-your-tenant_id).


4. After setting that value, subscribe your agent by running the following command:
   
    ```
    oc apply -f omegamon-subscribe.yaml
    ```

    The result is the bootstrapping of your agent to watsonx Orchestrate where it's then accessible for testing.

5. Verify that the bootstrapper pod is running in the `wxa4z-agents` namespace and has completed successfully.
   
    ![](_attachments/sub6.png)

6. Once verified, log into your watsonx Orchestrate environment and access your agent for testing.
   
    ![](_attachments/sub7.png)


