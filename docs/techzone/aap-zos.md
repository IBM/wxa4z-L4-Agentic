# Ansible Automation Platform (AAP) & z/OS

### Summary of the environment

The third lab environment you will use is the ***Ansible Automation Platform (AAP) & z/OS*** environment. This provides a pre-configured instance of both **Ansible Automation Platform (AAP)** and **Wazi aaS z/OS** deployed on IBM Cloud.

The two resources are provisioned together in the TechZone environment and enables users to manage and automate z/OS tasks and subsystems with various pre-installed Ansible playbooks. It includes a z/OS back-end (Wazi as a Service) with all needed pre-requisites to quickly get started.

This environment will come into play later on in the Lab when deploying your AI Agents. Each Agent has its own mechanism for accessing the back-end environment and performing tasks, gathering insights, etc.

As an example, you will later deploy the **IBM Z Upgrade Agent** which leverages z/OSMF APIs to your back-end Wazi z/OS system. As another example, the **IBM Z Support Agent** you will later deploy will connect to your Ansible Automation Platform (AAP) instance to automate the collection and transfer of z/OS dumps.

This environment will also be later used when building your own agent to automate the certificate renewal process on z/OS.


### Accessing the environment

Follow the below instructions to access your ***Ansible Automation Platform (AAP)*** environment. Instructions later on in the Lab will instruct you on accessing the **Wazi aaS z/OS** environment.

1. In the IBM Technology Zone portal, expand **My TechZone** and select **My Reservations**, or click the following link:
   
    <a href="https://techzone.ibm.com/my/reservations" target="_blank">ITZ My reservations</a>

    **IMAGE**

2. Click the **watsonx Assistant for Z Pilot - AAP & z/OS** tile.
   
    **IMAGE**

3. Locate and record the **AAP User Name (For UI access)** and **AAP User Password** fields.

    **IMAGE**

4. Record and then click the **Ansible Automation Platform UI** link.
   
    **IMAGE**

5. Enter the **Username** and **Password** that is recorded in step 3 and click **Log In**.
   
    **IMAGE**
   
6. Once logged in, you should be directed to the **Dashboard** view within the AAP Web console, as shown below:
   
    **IMAGE**








