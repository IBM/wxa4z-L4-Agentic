# Configuring the `secrets.data` variables

Scrolling down further in the **IBM Z OMEGAMON Insights Agent** section of your `values.yaml` file, you will see a **`secrets.data`** section with additional variables you must configure. It will look like what’s shown below:

```
secrets:
  data:
    AIOPS_BASE_URL: ""
    AIOPS_TOKEN: ""
    AGENT_AUTH_TOKEN: ""
```

The below table provides a summary of each of those variables that must be set, some of which you can use the corresponding default values for. For the first two variables, you will need to get the appropriate values to use from the instructor.

**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**AIOPS_BASE_URL** | Base URL of the zChatOps server instance | <a href="https://ibm.box.com/s/8o7x1zi9rxs5nrejla9ld6rhf1ek0sab" target="_blank">Internal only</a>
**AIOPS_TOKEN** | Bearer token for the ZChatOps server | <a href="https://ibm.box.com/s/8o7x1zi9rxs5nrejla9ld6rhf1ek0sab" target="_blank">Internal only</a>
**AGENT_AUTH_TOKEN** | Password for logging into your AAP Web console | "agent_auth_token"

*For the `AIOPS_BASE_URL` and `AIOPS_TOKEN` values, navigate to the link above which will direct you to a file containing the values for both variables.*

*Paste the provided values for the respective variable in your `values.yaml` file.*