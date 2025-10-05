* [Welcome](index.md)
* [Reserve the IBM Technology Zone environment](TechZoneEnvironment.md)
* Deploy and configure zAssistantDeploy
    * [Overview](zAssistantDeploy/Overview.md)
    * [Install the **oc** CLI and log into OpenShift](zAssistantDeploy/install-oc-utility.md)
    * [Install **IBM Certificate Manager**](zAssistantDeploy/install-cert-manager.md)
    * [Install the watsonx Assistant for Z **Operator**](zAssistantDeploy/install-wxa4z-operator.md)
    * [Deploy **secrets** for OpenSearch and Client Ingestion](zAssistantDeploy/deploy-secrets.md)
    * [Deploy **zAssistantDeploy** service](zAssistantDeploy/deploy-zAssistantDeploy.md)
    * [Verify deployment and acquire OpenSearch connection details](zAssistantDeploy/verify-deployment.md)
* Create an Assistant with zRAG documentation
    * [Overview](zRAG-Assistant/Overview.md)
    * [Access watsonx Orchestrate](zRAG-Assistant/access-wxo.md)
    * [Create a zRAG Assistant](zRAG-Assistant/create-assistant.md)
    * [Setup conversational search](zRAG-Assistant/setup-conv-search.md)
    * [Configure settings for conv search](zRAG-Assistant/configure-settings.md)
    * [Additional configuration](zRAG-Assistant/additional-config.md)
    * [Testing assistant's conv search capbilities](zRAG-Assistant/testing-conv-search.md)
* Ingest customer documentation
    * [Overview](ingest/Overview.md)
    * [Download and configure zAssist utility](ingest/download-zassist.md)
    * [Create Service Credentials for IBM COS](ingest/cos-service-credentials.md)
    * [Log into COS via ibmcloud utility](ingest/ibmcloud-utility.md)
    * [Create a storage bucket](ingest/create-storage-bucket.md)
    * [Upload docs to storage bucket](ingest/upload-docs.md)
    * [Execute doc ingestion](ingest/execute-ingestion.md)
    * [Test assistant Q&A with ingested documents](ingest/test-q&a.md)
* Prepare watsonx.ai services for agent deployment
    * [Create watsonx.ai Project](watsonx-ai/project.md)
    * [Create Deployment Space](watsonx-ai/deployment-space.md)
    * [Generate IBM Cloud API key](watsonx-ai/api-key.md)
    * [Retrieve watsonx Orchestrate Service Instance URL](watsonx-ai/service-instance-url.md)
    * [Locate your WML Base URL](watsonx-ai/wml-base-url.md)
* Execute agent deployment 
    * [Introduction to Agent Deployment](agentdeploy/Overview.md)
    * Setup for Agent Deployment
        * [Setup VS Code workspace](agentdeploy/setup.md)
        * [Overview of the wxa4z-agent-suite Helm charts](agentdeploy/wxa4z-agent-suite.md)
    * [Configure shared (global) agent variables](agentdeploy/configure-shared-variables.md)
    * Prepare for IBM Z Upgrade Agent
        * [Summary of agent capabilities](agentdeploy/upgrade-agent/overview.md)
        * [Configure the 'env' variables](agentdeploy/upgrade-agent/env.md)
        * [Configure the 'ptfJob' variables](agentdeploy/upgrade-agent/ptfJob.md)
        * [Configure the 'secrets.data' variables](agentdeploy/upgrade-agent/secrets-data.md)
        * [Configure the 'pvc' variable with storageClass](agentdeploy/upgrade-agent/pvc.md)
    * Prepare for IBM Z Support Agent
        * [Summary of agent capabilities]
        * [Configure the 'env' variables]
        * [Configure the 'secrets.data' variables]
    * Prepare for IBM Z OMEGAMON Insights Agent
        * [Summary of agent capabilities]
        * [Configure the 'env' variables]
        * [Configure the secrets.data variables]
    * Execute Agent Deployment
    * Access Agents and Test Demo Scenarios
        * [Access your deployed agents]
        * [Test the IBM Z Support Agent]
        * [Test the IBM Z OMEGAMON Insights Agent]
        * [Test the IBM Z Upgrade Agent]
    * [Embed Agent Chat in Web Page]
* Build your own agent using the Agent Development Kit (ADK)
    * [Introduction to the Agent Development Kit (ADK)]
    * [Installing and setting up ADK environment]
    * [Configuring AAP and z/OS certificates]
    * [Preparing VS Code workspace]
    * [Creating a connection and configuring credentials]
    * [Importing tools]
    * [Deploy the agent]
    * [Publish agent to 'Live' version]
    * [Test agent execution flow]