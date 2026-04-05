# Introduction to the Agent Development Kit (ADK)

Built on top of IBM watsonx Orchestrate, the watsonx Assistant for Z offering also enables flexible agent development for all users, empowering both business users and developers with a unified studio supporting low-code and pro-code development for key Z-specific use cases.

The **watsonx Orchestrate Agent Development Kit (ADK)** is a set of tools designed to make it easy to build and deploy agents. It is packaged as a Python library and command-line tool that allows builders to configure agents that run on the platform. The ADK also supports integrating agents and tools built on other frameworks.

The Agent Development Kit (ADK) is set of CLI utilities and python modules that helps you create agents and tools for watsonx Orchestrate. You can use these agents and tools across different watsonx Orchestrate offerings, including:

- watsonx Orchestrate on-premises
- watsonx Orchestrate IBM Cloud
- watsonx Orchestrate AWS
- watsonx Orchestrate Developer Edition

### ADK Components

The ADK has a CLI. The CLI can streamline the process of building, testing, and importing agents and tools

The ADK also provides a framework for developers to easily define new tools and agents programmatically.

1. Tools are defined using one of the available binding types (Python, OpenAPI, MCP, etc.) and then imported into the Orchestrate platform using the Orchestrate CLI.

2. Agents are defined using the ADK and then imported into the Orchestrate platform using the Orchestrate CLI. Agents use the tools defined in step 1.

3. Once an agent is imported, it can be used to start conversations with users either through the Orchestrate Agent Chat UI or through the Orchestrate API.

For more information on the ADK, reference the ADK documentation **<a href="https://developer.watson-orchestrate.ibm.com/" target="_blank">here</a>**.


### Lab Flow

For this Hands-on Agent Builder scenario, you will build multiple agents augmented with tools for calling various z/OSMF REST API endpoints to assist in verifying the status and health of different z/OS components. 

You will first build an ***IPL Validator Agent*** using the **pro-code** ADK approach which has two different pre-defined tools available to it. 

Following the successful deployment and testing of this agent, you will then create a new Orchestrator Agent using the **low-code** approach which will enable multi-agent collaboration. This agent, named the **z/OS Helper Agent**, will collaborate with the previously created **IPL Validator Agent** as well as the **zRAG Agent** which is a pre-built agent included in watsonx Assistant for Z and should've already been deployed in section [Execute agent deployment](../agentdeploy/execute-deploy.md). 


This hands-on lab shows how easy it is to create your own agents for key IBM Z use cases, in addition to the set of pre-built Z agents that ship with the product.

The steps you will execute include:

- Installing and setting up your local ADK environment
- Setting up VS Code workspace
- Configuring a connection and setting credentials
- Importing the provided tools
- Importing and testing the `IPL_Validator_Agent`
- Creating a custom `z/OS Helper Agent` which is an orchestrator agent with collaborator agents and additional tools