# Overview of the wxa4z-agent-suite Helm Charts

Now, within the **Explorer** view of VS Code, you should see the agent suite structure as shown below:

**IMAGE**


The **wxa4z-agent-suite** chart deploys a **suite of z/OS agents** with one command. Each agent remains an independent chart (own values, templates, and versioning) while the umbrella coordinates:

* **Single-command install/upgrade** for all enabled agents
* **Shared, reusable config & secrets** (optional, via `global.*`)


And below you can find a quick description of the repo layout:
```
wxa4z-agent-suite/ # <— umbrella chart
├─ Chart.yaml # lists all agent dependencies
├─ values.yaml # toggles & optional shared config/secrets
├─ templates/ # (usually minimal; e.g., optional global secrets) └─ charts/ # populated by helm dependency update
```

The `wxa4z-agent-suite/values.yaml` file is the file you will be modifying to configure your agents deployment. The steps taken in later sections include:

- Configuring the agents’ global settings (created once, used everywhere)
- Setting your registry entitlement key for foundational agents
- Disabling foundational agents not in scope of lab
- Configuring agent-specific values for each respective agent in scope for the lab deployment:
  - IBM Z Upgrade Agent
  - IBM Z Support Agent
  - IBM Z OMEGAMON Insights Agent
- Execute deployment via single `helm` command
- Verify agents’ deployment status