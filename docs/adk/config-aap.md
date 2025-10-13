# Configuring AAP and z/OS certificates

In this scenario, you will leverage 2 templates that have been pre-defined in your **Ansible Automation Platform (AAP)** environment. These 2 templates are:

- **z/OS Certs - List Cert**
  - Takes a certificate label as input and triggers an automation on z/OS to retrieve the certificate details, including the expiration date of the certificate
- **z/OS Certs - Search and Renew**
  - Automates the renewal process for a particular certificate on z/OS

In order to setup the scenario to demonstrate the capabilities of the agent you will later create, you will now leverage AAP to create a z/OS SITE certificate that is soon to be expiring.

1. Log into AAP by accessing your **Ansible Automation Platform UI** URL, and logging in with your **AAP User Name (For UI access)** and **AAP User Password** combination.
   
    *For help logging in, see **Section [Accessing the environment](../techzone/aap-zos.md#accessing-the-environment)**.*

2. Now you will create a **certificate authority (CA)** certificate to sign future SITE certificates. 
   
    Click **Templates** under the **Resources** section.

    **IMAGE**

3. Click the **launch** icon for the **z/OS Certs - Create Cert** template.
   
    **IMAGE**

4. On the **Survey** screen, modify the **Certificate Label** and **Type** fields with the values that follow and then click Next.
   
    **a.** `Certificate Label: TESTCA`

    **b.** `Type: CERTAUTH`

    ***Leave the defaults for all other fields.***

    **IMAGE**

5. Click **Launch**. 
   
    **IMAGE**

6. Review the output of the job. In the output of the playbook, notice that a new keyring is created, a certificate is created, and the certificate is connected to the keyring.
   
    **IMAGE**

    ***You have now successfully created your CA certificate, labeled ‘TESTCA’, that will be used to sign your new SITE certificate.***

7. Next, you will create an expiring certificate that uses the CA certificate that you just created.
   
    Return to the **Templates** tab and click the **launch** icon for the **z/OS Certs - Create Cert** template.

    **IMAGE**

8. On the **Survey** screen, modify the fields that follow with the values specified and then click **Next**.
   
    **a.** `Certificate Label: DEMOCERT`

    **b.** `Type: SITE`

    **c.** `Sign with: CERTAUTH`

    **d.** `Sign Label: TESTCA`

    **e.** `Common Name: company.com`

    **f.** `Expiration date: <enter a date that occurs within the next 30days. The date must be in the format YYYY-MM-DD>`

    ***Leave the defaults for all other fields.***

    **IMAGE**

    Unlike the first certificate you created which was *self-signed*, this certificate will be signed by the local certificate authority that uses the CA you created.

9. Click **Launch**. 
    
    **IMAGE**

10. Verify that the job was successful and inspect the output of the job.
    
    **IMAGE**

***You have now successfully created your ‘expiring’ SITE certificate, labeled ‘DEMOCERT’ which you will later use to demonstrate your agent’s capability of automating the certificate renewal process.***


