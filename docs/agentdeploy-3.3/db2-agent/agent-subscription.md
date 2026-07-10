# Subscribe agent to tenant

Finally, subscribe the agent to automate the bootstrapping of the **Db2 for z/OS Agent** to your watsonx Orchestrate environment. 


1. Once done, copy and paste the following into a file called `db2-subscribe.yaml`:

    ```
    apiVersion: wxa4z.watsonx.ibm.com/v1alpha1
    kind: AgentSubscription
    metadata:
      name: db2-agent-z-subscription
      namespace: wxa4z-agents
    spec:
      agent:
        agent_id: 'wxa4z:db2z-agent:agent'
        name: db2z-agent
        type: external
      tenant_id: ''
      wxa4z-core-services-namespace: wxa4z-zad
    ```

2. Set `tenant_id` to your environment's tenant id that you recorded [here](../setup.md#record-your-tenant_id).


4. After setting that value, subscribe your agent by running the following command:
   
    ```
    oc apply -f db2-subscribe.yaml
    ```

    The result is the bootstrapping of your agent to watsonx Orchestrate where it's then accessible for testing.

5. Verify that the bootstrapper pod is running in the `wxa4z-agents` namespace and has completed successfully.

6. Once verified, log into your watsonx Orchestrate environment and access your agent for testing.

