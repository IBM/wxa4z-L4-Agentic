# Overview - Ingesting customer documentation

With the ***OpenSearch*** service installed and configured in your assistant for the zRAG, you can now prepare for document ingestion, often referred to as the *bring-your-own-documentation* (BYOD) use case. This will demonstrate how clients can augment their assistant’s conversational search by creating an internal knowledge base with their own proprietary documentation. Using the client’s documentation allows the assistant to provide accurate responses to a range of questions not possible with only the default documentation available.

As an example, a client mentioned that their developers often need reference material on company-specific legacy code or company-specific syntax. The users must search through volumes of documentation to find it or look at old code. Also, there exists a need for their operational support group to quickly determine how to resolve technical issues using internal runbooks.

In this section, you will be able to demonstrate how watsonx Assistant for Z can assist developers and operational support personnel in finding answers about internal processes for code development and deployment. You will go through the steps of ingesting a set of sample documentation provided to illustrate this process.

**With previous versions of watsonx Assistant for Z**, document ingestion was executed using the ***zassist*** command-line utility to *ingest and load local files* directly to the client ingestion server. **Now with Version 3 of watsonx Assistant for Z**, this process is enhanced with client-side data ingestion through a remote S3 source to provide more effective embedding and allow for better performance.

***NOTE***: the supported file formats for document ingestion with a remote S3 source include *PDF*, *HTML*, *DOCX*, *CSV*, *XLS*, *XLSX*, *PPTX*, and *Markdown*.

In this section, you will be using a remote S3 source for the data ingestion process. Steps include:

- *Download and configure the zassist utility*
- *Configuring service credentials for your IBM Cloud Object Storage (COS) instance*
- *Creating a storage bucket*
- *Uploading documents to your storage bucket*
- *Executing the ingestion pipeline*