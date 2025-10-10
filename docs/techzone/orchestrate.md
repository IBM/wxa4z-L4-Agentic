# watsonx Orchestrate and other SaaS services

### Summary of the environment

The first Lab environment is a set of ***IBM Cloud SaaS resources*** we’ll refer to in this Lab as the **IBM watsonx Orchestrate environment**. The resources are dedicated to you and are all available within the same IBM Cloud account you’ve been granted access to. The SaaS resources used in this Lab guide consist of the three components below:

1. **watsonx Orchestrate**
   
    IBM watsonx Assistant for Z is powered by watsonx Orchestrate, a generative AI platform for building, accessing and testing AI agents and assistants. As an on-prem solution, the watsonx Orchestrate component of watsonx Assistant for Z is deployed on Red Hat OpenShift and the IBM Cloud Pak platform. With version 3 of the offering comes the ability to connect your agents to a broad range of components, including IBM Z infrastructure, middleware, tools, third-party software and custom applications, forming the foundation for scalable and secure enterprise operations.

    The chat interface allows users to engage with the system through conversational AI and goal-oriented agents. It provides an intuitive and responsive way to access the platform’s capabilities.

    For the purpose of the Lab, you will be using a **dedicated SaaS tenant of watsonx Orchestrate on IBM Cloud** where you will be able to deploy your AI agents for watsonx Assistant for Z, as well as zRAG assistants to demonstrate various use cases.

    Later in the lab you will also use your watsonx Orchestrate environment to build your own agents for a set of Z specific use cases.


2. **watsonx.ai Runtime (WML)**
   
    As mentioned above, you will be leveraging a cloud-based deployment to configure and execute various use cases supported by watsonx Assistant for Z. As such, you will leverage the **watsonx.ai Runtime** SaaS component on IBM Cloud to provide the underlying compute resources and services to power the AI agents you deploy. This provides a way to enable the Agentic AI features of the solution for the purposes of demos and pilots without having to install the full solution on-prem.

3. **IBM Cloud Object Storage (COS)**
   
    The last IBM Cloud SaaS service in scope for the Lab is **IBM Cloud Object Storage (COS)** which is used for ingesting customer documentation into the zRAG component of watsonx Assistant for Z. It will be used to demonstrate how clients can augment their agent and assistants’ conversational search capabilities by creating an internal knowledge base with their own documentation. This allows users to get insightful responses to a rnage of questions not possible with the default documentation within the zRAG.

### Accessing the environment





