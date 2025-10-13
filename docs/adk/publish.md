# Publish agent to 'Live' version

Before testing the agent's execution flow within the watsonx Orchestrate Chat, you will first access your agent (which should currently be the `Draft` version) and publish it to the `Live` version. 

1. Navigate back to your **watsonx Orchestrate** environment UI so that you see the following:
   
    **IMAGE**

2. Within the watsonx Orchestrate UI, navigate to the **Agent Builder** view by clicking on **Build -> Agent Builder**.
   
    **IMAGE**

3. Once in the **Agent Builder**, click on your newly deployed agent, labeled **zOS_Certificate_Agent** as shown below:
   
    **IMAGE**

4. Then you will be in the ***Preview*** mode of your agent as the agent was created in **draft** mode only (prior to deploying). 
   
    In the Agent definition, scroll down and view the different settings that were automatically configured based on the definitions of the Agent yaml file you used.

    In the **Tools** section, verify that all 3 tools you deployed are present and available to the agent:

    **IMAGE**

    Also notice the **welcome message** you configured in the `zOS_Cert_Agent.yaml` file:

    **IMAGE**

5. After verifying the agent definitions, you can deploy the agent in the “Live” environment. 
   
    To do this, click **Deploy** at the top-right of the page.

    **IMAGE**

6. In the new window, click on the ‘pencil’ icon next to your ***ansible*** connection to modify the connection for your “Live” environment.
   
    **IMAGE**

7. In the **Configure live connection** window, set the following:
   
    **a.** `Authentication type:` set to “Basic Auth”

    **b.** `Server URL:` copy and paste your `<AAP UI URL>`

    **c.** `Credential type:` set to `Team credentials`

    **d.** `Username:` set to `admin`

    **e.** `Password:` copy and paste your `<AAP User Password>`

    Then click **Connect**. 

    **IMAGE**

8. After clicking **Connect**, wait until you see a “Connected” message appear at the bottom, then click **Save**.
   
    **IMAGE**

9. Finally, click **Save and close**.
    
    **IMAGE**

10. Lastly, back at the **Deploy Agent** page, you should now see a green check-mark next to the “Live” connection. 
    
    Click **Deploy**.

    **IMAGE**

11. After a few seconds, the agent will finish deploying and you will see a `Success!` message as shown below. Wait until the deployment completes. ***Note:** this may take up to 30 seconds or so.*
    
    **IMAGE**

12. Once the deployment completes, navigate back to the agent chat view by clicking on **Chat** in the menu.
    
    **IMAGE**

13. Click on the **‘Agents’** drop-down and select your deployed agent, labeled **zOS_Certificate_Agent**.
    
    **IMAGE**

***You are now ready to begin the demo scenario - follow the steps in the next section.***


