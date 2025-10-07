# Configuring the `env` variables

Within your `values.yaml` file, locate the section for the **IBM Z OMEGAMON Insights Agent** as shown below:

```
# ---------------------------------------------------------------------------- #
# Default: omegamon-insights-agent
# ---------------------------------------------------------------------------- #
omegamon-insights-agent:
  enabled: true
  image:
    # additional agent-specific config....
```

Within this agent’s section of `values.yaml` scroll down to the **`env`** variable section which by default should look like what’s shown below:

```
env:
  DEPLOYMENT_TYPE:
```

Below is a brief summary of this variable. Keep the default value of **"cloud"** set for this variable as you will be accessing this external agent from WxO SaaS.

**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**DEPLOYMENT_TYPE** | Type of deployment (options include 'on-prem' and 'cloud') | "cloud"

***ACTION:** set the above variable to the default value in your values.yaml file under the ‘omegamon-insighst- agent’ section (in the env variables section)*