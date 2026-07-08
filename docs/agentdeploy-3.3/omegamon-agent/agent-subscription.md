# Subscribe agent to tenant

Finally, subscribe the agent to automate the bootstrapping of the **OMEGAMON Insights Agent** to your watsonx Orchestrate environment. 

### BEFORE CREATING AGENT SUBSCRIPTION - REMOVE "VIRTUAL-MODEL" FROM BOOTSTRAP CONFIGMAP

1. To do this, copy and paste the following into a file called `omegamon-subscribe.yaml`:

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

2. Set `tenant_id` to your environment's tenant id that you recorded [here](../setup.md#record-your-tenant_id).


3. After setting that value, subscribe your agent by running the following command:
   
    ```
    oc apply -f omegamon-subscribe.yaml
    ```

    The result is the bootstrapping of your agent to watsonx Orchestrate where it's then accessible for testing.

   


