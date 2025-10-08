# Access your deployed agents

By leveraging watsonx Assistant for Z for the pre-built Z agents, each agent deployment is automatically ‘bootstrapped’ to your watsonx Orchestrate environment where the agents are immediately accessible for testing.

In this section, you will access each of the deployed agents, test the scenarios, and learn how to embed your agent’s chat within a webpage for external access.

1. Access your **watsonx Orchestrate** UI within the IBM Cloud web console. Once logged in, you should see the **Agent Chat** screen as shown below:
   
    **IMAGE**

    The **Agent Chat** screen is where you can go to interact with your ‘deployed’ agents.

    ***Note:*** each of the agents you previously deployed are bootstrapped to WxO as ‘draft’ versions of each of the agents. Once each agent has been successfully tested within WxO, you can then deploy each agent to the ‘live’ version to make it externally accessible.

2. To access the ‘Draft’ version of each of your 3 agents, click on the hamburger icon in the top-left corner of the WxO UI, then navigate to **Build --> Agent** Builder, as shown below:
   
    **IMAGE**

3. Once in the Agent Builder page, verify you can see a tile for each of your deployed agents:
   
    - IBM Z Upgrade Agent
    - IBM Z Support Agent
    - IBM Z OMEGAMON Insights Agent
  
    **IMAGE**

    ***Note:** by default, you may also see the ‘AskOrchestrate’ agent within your agent list. This can be ignored*.

