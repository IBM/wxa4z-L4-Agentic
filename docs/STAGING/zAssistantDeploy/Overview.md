# Overview of *zAssistantDeploy*

IBM watsonx Assistant for Z leverages **Conversational AI** to provide accurate answers to questions related to IBM Z with detailed steps and links to enhance learning. This feature is based on Large Language Model (LLM) coupled with domain-specific Retreival-Augmented Generation (RAG) which augments the LLM with IBM Z domain- specific knowledge base and information.

As an Openshift-based solution, watsonx Assistant for Z provides this capability via the **zAssistantDeploy** service on OpenShift. With the purchase of watsonx Assistant for Z, customers acquire entitlement to the watsonx Assistant for Z **operator** which is usd to deploy and configure the zAssistantDeploy service.

**zAssistantDeploy** provides an OpenSearch deployment that is pre-installed with IBM Z documentation, along with a data ingestion service that can be used to load your own documents into the knowledge base. The solution’s search parameters can then be configured to fetch content from those ingested documents.

In this section, you will be deploying and configuring the **zAssistantDeploy** component of the solution on your provided OpenShift cluster to enable the zRAG capabilities for conversational AI.

*Steps include:*

- Accessing and logging into your OpenShift cluster from your local workstation
  
- Installing IBM Cert Manager on your cluster
  
- Installing the watsonx Assistant for Z Operator
  
- Deploying secrets required for OpenSearch and the Client Ingestion service
  
- Deploying the zAsssistantDeploy service on your cluster
  
- Verifying successful deployment and acquiring your OpenSearch connection details

Following this section, you will learn how to connect assistants and agents to your OpenSearch instance in order to configure conversational search leveraging the zRAG, as well as the ability to ingest custom documentation into the RAG database.