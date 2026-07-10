# Subscribe agent to tenant

Finally, subscribe the agent to automate the bootstrapping of the **Upgrade Agent** to your watsonx Orchestrate environment. 

### BEFORE CREATING AGENT SUBSCRIPTION - REMOVE "VIRTUAL-MODEL" FROM BOOTSTRAP CONFIGMAP


1. To do this, copy and paste the following into a file called `upgrade-subscribe.yaml`:

    ```
    apiVersion: wxa4z.watsonx.ibm.com/v1alpha1
    kind: AgentSubscription
    metadata:
      name: upgrade-agent-z-subscription
      namespace: wxa4z-agents
    spec:
      agent:
        agent_id: 'wxa4z:upgrade-agent:agent'
        name: upgrade-agent
        type: external
      tenant_id: 'dc6bd41c-faca-41b8-8483-a5676d4380dc'
      wxa4z-core-services-namespace: wxa4z-zad
    ```


2. Set `tenant_id` to your environment's tenant id that you recorded [here](../setup.md#record-your-tenant_id).


3. After setting that value, subscribe your agent by running the following command:
   
    ```
    oc apply -f upgrade-subscribe.yaml
    ```

    The result is the bootstrapping of your agent to watsonx Orchestrate where it's then accessible for testing.

4. Verify that the bootstrapper pod is running in the `wxa4z-agents` namespace and has completed successfully.

5. Once verified, log into your watsonx Orchestrate environment and access your agent. Test prompts, i.e.:
   
    - "s

