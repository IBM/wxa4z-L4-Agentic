# Overview

### watsonx Assistant for Z Architecture

IBM® watsonx Assistant for Z is powered by IBM watsonx Orchestrate® that is built on Red Hat® OpenShift® and IBM Cloud Pak® Platform.

At the architectural level, watsonx Assistant for Z introduces an Orchestrator agent that directly connects IBM Z agents and MCP servers. This enables AI capabilities for a broad range of components across the IBM Z ecosystem, including Infrastructure, Middleware, Tools, third-party software, and custom applications, forming the foundation for scalable and secure enterprise operations.

![](_attachments/watsonx.ai-architecture.png)


The Orchestrator agent serves as the central hub of the watsonx Assistant for Z architecture. It coordinates interactions across all components, ensuring seamless communication and data flow. It connects to key services such as zRAG, Topology, and Identity Management, as well as both IBM and third-party software systems, enabling a unified and intelligent automation experience.

The system includes IBM Z Software agents embedded within IBM Z products, foundational agents that are ready for immediate deployment, third-party agents developed by external vendors, and custom agents created by users to meet unique operational needs. Together, these agents extend the platform’s flexibility and intelligence.

The chat interface allows users to engage with the system through conversational AI. It provides an intuitive and responsive way to access the platform’s capabilities.

Additionally, the architecture includes the following components:

- **Retrieval Augmented Generation (zRAG)** - A component that augments LLM with the knowledge based on IBM Z documentation and creates IBM Z context aware responses to the questions.

- **Topology** - The system topology feature interacts with z/OSMF APIs to collect information about the system’s structure and the versions of installed software. This foundational data helps users gain a basic understanding of their environment, which is essential for learning and managing IBM Z systems effectively.

- **Identity Management** - Identity Management plays a vital role in ensuring system security and governance. It manages user identities and enforces access controls, allowing only authorized users to interact z/OSMF and OMEGAMON APIs.

## Section overview

For the purpose of demos and pilots, you will be using the watsonx.ai Runtime SaaS version on IBM Cloud to provide the IFM layer to connect your agents and services to the chosen LLMs and underlying  resources. A cloud-based deployment is used to configure and execute various use cases supported by watsonx Assistant for Z to enable the Agentic AI features of the solution without having to install the full solution on-prem, as a customer normally would in production. 

The steps in this section will walk you through the creation of the following required secrets which will be used later on:

- watsonx.ai Project

- Deployment Space

- Cloud API Key

- watsonx Orchestrate Service Instance URL

- WML Base URL




