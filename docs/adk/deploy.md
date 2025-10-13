# Deploy the agent

In the ADK, agents can use tools to perform complex tasks defined by users. Each agent has a name and description that is configured, helping users identify each agent they can use to perform certain actions.

In this section, you will define an agent named **zOS_Certificate_Agent** that leverages the tools you have imported into the ADK environment to help users quickly identify certificate information and assist with the renewal process of expiring certificates, all from a single chat and using natural language.

1. Within VS Code, click on the `zOS_Cert_Agent.yaml` file under the ‘Agents’ sub-folder to view the contents.
   
    **IMAGE**

2. You should then be able to see the agent definition as shown below:
   
    **IMAGE**

    *Lets go over each of the sections...*

    **IMAGE**

    For further details on building agents with the ADK, you can reference the ADK guide <a href="https://developer.watson-orchestrate.ibm.com/agents/overview" target="_blank">here</a>.

3. Finally, deploy the agent by issuing the following command within your VS Code Terminal command-line:
   
    ```
    orchestrate agents import -f Agents/zOS_Cert_Agent.yaml
    ```

4. If executed correctly, you should see a message similar to below:
   
    **IMAGE**

**Congratulations! You’ve deployed your first agent using the ADK and are now ready to test the execution flow leveraging the previous certificates you’ve setup on z/OS using Ansible Automation Platform.**

