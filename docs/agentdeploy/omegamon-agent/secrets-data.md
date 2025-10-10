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
**AIOPS_BASE_URL** | Base URL of the zChatOps server instance | ask instructor
**AIOPS_TOKEN** | Bearer token for the ZChatOps server | ask instructor
**AGENT_AUTH_TOKEN** | Password for logging into your AAP Web console | agent_auth_token