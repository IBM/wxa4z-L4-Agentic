# Subscribe agent to tenant

Finally, subscribe the agent to automate the bootstrapping of the **OMEGAMON Insights Agent** to your watsonx Orchestrate environment. 

To do this, copy and paste the following into a file called `omegamon-subscribe.yaml`:

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

Set `tenant_id` to your environment's **tenant id**. Two ways of finding it:

- In your watsonx Orchestrate **Service Instance URL**, the `tenant_id` appears as the final end. For example:
   
    `https://api.us-south.watson-orchestrate.cloud.ibm.com/instances/<tenant_id>`


- In your OpenShift web UI, the automatically create namespace contains the value of your tenant (i.e. `wxa4z-<tenantid>`).


After setting the `tenant_id`, subscribe your agent by running:

`oc apply -f omegamon-subscribe.yaml`

The result is the bootstrapping of your agent to watsonx Orchestrate where it's then accessible for testing. 

   


