# Subscribe agent to tenant

Finally, subscribe the agent to automate the bootstrapping of the **Automation Insights Agent** to your watsonx Orchestrate environment. 

!!! Warning "Prior to subscribing agent...."

    Prior to subscribing the agent, ensure you first complete the step outlined <a href="https://ibm.github.io/wxa4z-L4-Agentic/agentdeploy-3.3/llm-config" target="_blank">here.</a>


1. Copy and paste the following into a file called `automation-subscribe.yaml`:

    ```
    apiVersion: wxa4z.watsonx.ibm.com/v1alpha1
    kind: AgentSubscription
    metadata:
      name: automation-agent-z-subscription
      namespace: wxa4z-agents
    spec:
      agent:
        agent_id: wxa4z:automation-agent-z:agent
        name: automation-insights-agent
        type: external
      tenant_id: ''
      wxa4z-core-services-namespace: wxa4z-zad
    ```

2. Set `tenant_id` to your environment's tenant id that you recorded [here](../setup.md#record-your-tenant_id).


3. After setting that value, subscribe your agent by running the following command:
   
    ```
    oc apply -f automation-subscribe.yaml
    ```

    The result is the bootstrapping of your agent to watsonx Orchestrate where it's then accessible for testing.

4. Verify that the automation insights agent **bootstrapper** pod is running in the `wxa4z-agents` namespace and has completed successfully.
   
5. Once verified, log into your watsonx Orchestrate environment and access your agent for testing.
   