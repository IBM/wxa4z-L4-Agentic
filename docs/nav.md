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
    * PLACEHOLDER
* Execute agent deployment 
    * Introduction to Agent Deployment
    * Setup for Agent Deployment
        * Setup VS Code workspace
        * Overview of the wxa4z-agent-suite Helm charts
    * Configure shared (global) agent variables
    * Prepare for IBM Z Upgrade Agent
        * Summary of agent capabilities
        * Configure the 'env' variables
        * Configure the 'ptfJob' variables
        * Configure the 'secrets.data' variables
        * Configure the 'pvc' variable with storageClass