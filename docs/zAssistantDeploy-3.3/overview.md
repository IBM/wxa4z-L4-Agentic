# Overview

IBM watsonx Assistant for Z, version 3.3, provides multi-tenancy support for isolating core services by tenants. This allows for compliance and security across end-users and the data they interact with. 

As this is an on-prem product, the look and feel won't be exactly as experienced by end-users deploying on-prem, but many of the same capabilities are supported for demo and pilot purposes. 

In this section, you will deploy the core services of watsonx Assistant for Z onto your OpenShift cluster, and create a **zRAG Tenant** with automated bootstrapping of the zRAG Agent, along with a dedicated instance of OpenSearch and the Client Ingestion service. 

To accomplish this, an automated script is provided to you in order to automate the deploy of the watsonx Assistant for Z multi-tenant operator on a SaaS cluster, with the zRAG agent provisioned on Orchestrate as part of the bootstrapper flow. 

The ***deploy-operator-saas.sh*** script will automate everything needed to successfully deploy the core ZAD services and bootstrap the zRAG Agent within your tenant and onto watsonx Orchestrate SaaS. 


## Pre-requisites and setup

### Completed setup of watsonx.ai services

Prior to kicking off the automation script, you will need to gather and record the following information which you would've completed in the previous section. You will be prompted for this during execution.

- **Deployment space id** from Section.....
- **IBM Cloud API Key**
- **watsonx Orchestrate Service Instance URL**
- **WML_URL**

### Download *deploy-operator-saas.sh* script

Next, download the <a href="https://ibm.box.com/s/3v5id2girkzyol9grjicoqj5e07784dp
" target="_blank">deploy-operator-saas.sh</a> automation script to your local machine. 

This shell script targets clusters using watsonx.ai SaaS for inferencing rather than the on-prem AIO inference gateway. 

Once downloaded, open up the script in a Visual editor of your choice, preferable VS Code. 


### Log into OpenShift cluster and install cert-manager

Next, log into your OpenShift cluster and install the **Red Hat cert-manager operator**. 

1. Log into your ***OpenShift*** cluster via web console by following the instructions ***[here](../techzone/sno.md#accessing-the-environment)***.


2. Click the `kube:admin` profile drop-down and click **Copy login command**.
   
    ![](_attachments/oc4.png)

3. Click **Display Token**.
   
    ![](_attachments/oc5.png)

4. Select and copy the ***Log in with this token*** string.

    *For most operating systems, double-click the value, then right-click and select **Copy***.

    ![](_attachments/oc6.png)

5. Within your previously opened VS code session, open a terminal window and paste the command and press **enter**. 

6. Once you've logged into your cluster via the command-line, navigate back to the web console.

7. In the OpenShift web console, click **Operators** and then select **OperatorHub**.
   
    ![](_attachments/cert1.png)

8. Click the **Project** to pull-down menu and click the **Show default projects** toggle.
   
    ![](_attachments/cert2.png)

9. Scroll down and select **openshift-marketplace**.
   
    ![](_attachments/cert3.png)

10. Enter `cert-manager` in the search field and then click the **cert-manager Operator for Red Hat OpenShift** tile.
   
    ***Note:** it may take a minute or 2 for the tile to appear. Click on a different tab and go back to it to refresh*.
   
    ![](_attachments/rh1.png)

11. Click **Install**.
   
    ![](_attachments/rh2.png)

12. Keep the default settings and click **Install**.
   
    ![](_attachments/rh3.png)

    ***NOTE:*** *the installation process takes a few minutes. DO NOT continue until you see the following message: `Installed operator: ready for use`.*

    ![](_attachments/rh4.png)


Once completed, you can move on. 

### Obtain `tz-pull-secret` entitlement key

Finally, as this is a modified version of the operator deployment for SaaS based deployments, there are a set of images designed specifically for this workflow that you'll use. In order to pull the necessary images, you will need to retrieve the entitlement key to the image registry. You will also be prompted for this during the script execution. 

Retrieve the entitlement key from here: https://ibm.box.com/s/7sm5v6nfzrm7r0vz64zyb81cmgx1x40e

**Note: ** you will supply this entitlement key when the script prompts you for the `tz-pull-secret` entitlement key. 

