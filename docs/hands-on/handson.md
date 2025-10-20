# Enabling hands-on client access for supported agents

As part of a client engagement (i.e. customer pilot), you may have a need to provide hands-on access to one or more of the supported watsonx Assistant for Z agents not covered in earlier sections. This section is intended to walk you through the process of setting up pre-deployed (hosted) agents ***that you can import into your instance of watsonx Orchestrate***. This allows for a way to provide your client hands-on access for a **defined amount of time** for the purpose of use case discovery and execution. 

!!! Tip "Existing agent demos..."

    The hosted agents discussed in this section are already available for IBMer & Business Partner access <a href="https://techzone.ibm.com/collection/ibm-watsonx-assistant-z/journey-step-1-briefings-and-demos" target="_blank">on TechZone here</a>. This section is intended to guide Tech Sellers on extending hands-on access to these hosted agents externally, which can be included as part of a pilot engagement.

*The process consists of 2 steps:*
- Importing the pre-hosted agents into your watsonx Orchestrate environment using the Agent Development Kit (ADK)
- Embedding the agent chat in an HTML file to share with a client for external access

***NOTE:*** *It's crucial that you clearly define the amount of time clients will have access. Following the end time, you must **make sure you clean up the environment** and **delete your imported agent** to prevent persisted access*.  


### Importing the hosted agents into watsonx Orchestrate using the ADK

As mentioned, there may be a need to extend access to a set of demo agents that you are not able to deploy yourself and are not documented in this guide (i.e. infrastructure requirements, network connectivity challenges, etc.). This section provides a way to import pre-deployed agents used for demos into your own watsonx Orchestrate environment using the ADK. 

For each of the agents discussed in this section, there are a set of **YAML** files which define the following:
- an **Orchestrator (native)** agent which the end-user interacts with
- the **external agent(s)** which point to a hosted agent deployed on OpenShift you import to demonstrate various use cases. 

The process of using the **ADK** to import the agents into your watsonx Orchestrate environment firstly involves importing the 1 or more external agents (as collaborators), and secondly, importing the orchestrator agents which you will publish and embed into a web chat. 

This section documents the process of importing the following pre-deployed agents into your watsonx Orchestrate environment: 
- IBM Db2 for z/OS Agent
- IBM Operations Agent for Z
- IBM IMS Agents

1. The first step before importing agents are to activate the ADK using your watsonx Orchestrate environment. You may have already done this in Section ***[Installing and setting up your ADK environment](../adk/setup.md)***. 
   
    As a reminder this can be done using the following command: 

    ```
    orchestrate env add -n <env name> -u <your Service Instance URL> --type ibm_iam --activate
    ```

    For more details on how to activate the ADK using your watsonx Orchestrate environment, see the <a href="https://developer.watson-orchestrate.ibm.com/getting_started/installing#ibm-cloud" target="_blank">ADK documentation here</a>.


2. One activated, you can download the appropriate Agent folder containing the agent YAML files for each:
   
    IBM Db2 for z/OS Agent 
    <a href="https://developer.watson-orchestrate.ibm.com/getting_started/installing#ibm-cloud" target="_blank">ADK documentation here</a>.

    IBM Operations Agent for Z 

    IBM IMS Agents


IBM Db2 for z/OS Agent files: https://ibm.box.com/s/2i295wv0obbtjctdi6p30wlojwlcnee0

IBM IMS Agent files: https://ibm.box.com/s/ryufp5bkbtmjcjl25p8k45ly62xnv641

IBM Operations Agent for Z files: https://ibm.box.com/s/1fyccoymkz2ghshdu4okreh491lijoqw




### Embedding the agent chat for external access
- first, publish to the Live environment
- Test the agent using the demo script on TechZone (provide link)


### Cleanup the agent deployment