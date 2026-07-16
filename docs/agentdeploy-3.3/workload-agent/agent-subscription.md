# Subscribe agent to tenant

Finally, subscribe the agent to automate the bootstrapping of the **Workload Scheduler Agent** to your watsonx Orchestrate environment. 


1. Copy and paste the following into a file called `workload-subscribe.yaml`:

    ```
    apiVersion: wxa4z.watsonx.ibm.com/v1alpha1
    kind: AgentSubscription
    metadata:
      name: workload-agent-z-subscription
      namespace: wxa4z-agents
    spec:
      agent:
        agent_id: wxa4z:workload-scheduler-agent-z:agent
        name: workload-scheduler-agent-z
        type: external
      tenant_id: ''
      wxa4z-core-services-namespace: wxa4z-zad
    ```

2. Set `tenant_id` to your environment's tenant id that you recorded [here](../setup.md#record-your-tenant_id).


3. After setting that value, subscribe your agent by running the following command:
   
    ```
    oc apply -f workload-subscribe.yaml
    ```

    The result is the bootstrapping of your agent to watsonx Orchestrate where it's then accessible for testing.

4. Verify that the workload scheduler insights agent **bootstrapper** pod is running in the `wxa4z-agents` namespace and has completed successfully.
   
5. Once verified, log into your watsonx Orchestrate environment and access your agent for testing.
   