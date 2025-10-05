# Create watsonx.ai Project

Now that you’ve tested the conversational search features of your zRAG assistant and tested document ingestion
using the sample documents provided, you will prepare for agent deployment of a subset of foundational agents
entitled with watsonx Assistant for Z. As part of the deployment, you will first need to configure your ***watsonx.ai
services*** and captured the needed secrets to provide in your agents’ deployment. This section covers this process
in detail.

***NOTE:*** as you complete each following sub-section, ensure you’re recording all of the values being
referenced in a local notepad. This will make life much easier later on during the agent deploy


The first secret needed in configuring your watsonx Assistant for Z agents for deployment is retrieving your
`<WATSONX_PROJECT_ID>`. This step will walk you through creating a **Project** in **watsonx.ai** and retrieving
that secret for later use. 

1. Navigate to your ***Resources List*** in the IBM Cloud web console using the first Lab environment. Reference
the instructions in `Section 3.1: Accessing IBM watsonx Orchestrate Trial/Standard Plan` for a reminder on
how to get to your **Resource List**.