# Configuring the `secrets.data` variables

Scrolling down further in the **compiler-fix-finder-agent** section of your `values.yaml` file, you will see a **`secrets.data`** section with an additional variable you must configure. It will look like what’s shown below:

```
secrets:
  data:
    AGENT_AUTH_TOKEN: ""
```

### Setting the `AGENT_AUTH_TOKEN` variable

Set the `AGENT_AUTH_TOKEN` variable to `compiler_auth_token` or any unique value of your choice. This is the token used by the agent-controller to register this agent with WxO. 

