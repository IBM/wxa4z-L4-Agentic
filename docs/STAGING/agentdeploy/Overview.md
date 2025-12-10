# Overview of Agent Deployment

IBM watsonx Assistant for Z delivers the next level of productivity with Agentic AI, providing one place to build, manage and run all your agents. Agents are designed to understand user intent, collaborate, and provide comprehensive responses.


With watsonx Assistant for Z, users have available a set of pre-built Z domain-specific agents that cover two categories:

- **Foundational Agents** - enabled by default and covered by the IBM watsonx Assistant for Z entitlement

- **Prebuilt IBM Z Product Agents** - require separate product entitlements (e.g. Db2 for z/OS agent, IntelliMagic Agent for Z)

## Foundational Agents

**Foundational agents** work together to collect all required information by leveraging integrated tools, and then provide a detailed and comprehensive answer to any query, enabling more informed decision making with limited human intervention.

These agents are enabled by default and are available upon installing watsonx Assistant for Z. 

***Below is a summary of the foundational agents that are available with the product:***

**Agent** | **Description**
--- | --- 
**zRAG Agent** | The zRAG Agent delivers technical assistance for mainframe and enterprise systems through the Watson Assistant for Z chat interface. It utilizes the zRAG (z/OS Retrieval-Augmented Generation) knowledge base to provide precise, citation-backed answers by integrating IBMs official documentation repositories with custom enterprise content.
**IBM Z Support Agent** | The Support Agent enables users to run Ansible playbooks through Ansible Automation Platform, triggered by user input. Supported playbooks include: collecting z/OS dumps from a specified z/OS address space, and transfering a dump to IBM Support. Additionally, the agent provides functionality to retrieve the status of initiated Ansible jobs and access job logs for monitoring and troubleshooting.    
**IBM Z OMEGAMON Insights Agent** | The IBM Z OMEGAMON Insights Agent allows system programmers to access and analyze system data directly through the watsonx Assistant for Z chat interface. By leveraging OMEGAMON data, it delivers accurate insights that help streamline system monitoring and decision-making.
**IBM Z Upgrade Agent** | The IBM Z Upgrade Agent enables system programmers to perform z/OS upgrades through the watsonx Assistant for Z chat interface. It provies precise responses by leveraging z/OSMF APIs and client-specific documentation stored in the zRAG.
**IBM Z Automation Insights Agent** | The Automation Insights Agent allows system programmers to retrieve and analyze system data through the watsonx Assistant for Z chat interface. It delivers accurate insights by leveraging data from the Automation and NetView domains, helping users better understand system behavior and performance.
**IBM Z Workload Scheduler Insights Agent** | The Workload Schduler Insights Agent enables system programmers to access and analyze workload and engine-relatd information through the watsonx Assistant for Z chat interface. It helps users gain visibility into scheduling operations and system activity, supporting more informed decision-making and faster issue resolution.


## Prebuilt IBM Z Product Agents

The Prebuilt IBM Z Product Agents across various IBM Z software solutions simplify complex tasks and enhance productivity through natural language interactions. Together, these agents streamline operations, deliver actionable insights, and make mainframe technologies more accessible and user-friendly.

These agents require separate product entitlements in order to deploy and run on the watsonx Assistant for Z platform, and can be enabled as needed, according to each agent’s specific requirements.

***Below is a summary of the Pre-built IBM Z Product Agents:***

**Agent** | **Description**
--- | --- 
**IBM CICS Transaction Server Agents for Z** | The CICS agent is capable of answering questions related to CICS topology and assisting with problem diagnosis by interpreting transaction error codes. It helps users understand the structure and relationships within the CICS environment and supports troubleshooting by providing insights based on specific error inputs.
**IBM Db2 for z/OS Agent** | The IBM Db2 for z/OS Agent is an AI-powered assistant that allows users to access real-time information about Db2 for z/OS subsystems and database objects through a prompt-driven conversational interface. For instance, you can ask about the current value of a subsystem parameter, identify which buffer pool an index uses, or check if any utilities are running on a subsystem. Along with delivering the requested information, the agent also explains the approach it used to derive the response
**IBM IMS Agents** | IBM IMS Agents software handles general queries related to IMS command syntax and formatting. It also provides real-time visibility into the operational status of IMS systems, helping accelerate troubleshooting by simplifying the diagnostic process.
**IBM IntelliMagic agent for Z** | A system designed to recommend relevant IBM Z IntelliMagic Vision for z/OS charts and reports based on a user-specified topic or issue. These visualizations deliver comprehensive insights into the IBM Z environment, covering both performance and configuration aspects. The recommended outputs may include health evaluations, exception notifications, performance indicators, and configuration data. The system spans key components such as Db2, CICS, IMS, FICON Directors, and Storage Systems.
**IBM Operations Agent for Z** | Monitors key system metrics—including CPU usage, I/O activity, transaction volumes, response times, and storage availability. It identifies resource-heavy transactions and low-storage conditions, while tracking limits like MAXTASKS and concurrent transactions. Users gain visibility into active CICS regions, CICSPlexes, Sysplexes, LPARs, and workloads in z/OS environments. It provides Workload Management (WLM) analytics, covering transaction rates, response times, performance indexes, and goal achievement. Service classes missing objectives are flagged, and critical events are reported.
**Functional Testing Agent (TAZ)** | This AI-powered solution uses natural language inputs to automatically generate UI-driven functional test cases. By leveraging agentic AI, it transforms written requirements and manual test descriptions into executable Java Galasa tests. Integrated with Microsoft Visual Studio Code (VS Code), the tool enables users to explore transaction screen capabilities and seamlessly generate functional tests for them.


**IMPORTANT**

***For the purpose of this lab, the set of agents used for deployment will be scoped to the three following Agents:***

- zRAG Agent
- IBM Z Upgrade Agent
- IBM Z Support Agent
- IBM Z OMEGAMON Insights Agent
- Db2 for z/OS Agent


!!! Tip "Official Agent deployment documentation"
    
    This lab guide documents all the steps required to deploy your watsonx Assistant for Z **AI Agents** using the referenced TechZone environments. The **official IBM guidance and documentation** resides in the public **IBM Z AI Agents - Deployment Guide** Git Hub repository. Feel free to reference this <a href="https://github.com/IBM/z-ai-agents" target="_blank">here</a>.