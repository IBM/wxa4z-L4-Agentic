# Configuring the `secrets.data` variables

Scrolling down further in the **IBM Z OMEGAMON Insights Agent** section of your `values.yaml` file, you will see a **`secrets.data`** section with additional variables you must configure. It will look like what’s shown below:

```
secrets:
  data:
    AIOPS_BASE_URL: ""
    AIOPS_TOKEN: ""
    AGENT_AUTH_TOKEN: ""
```

The below table provides a summary of each of those variables that must be set, some of which you can use the corresponding default values for. For the first two variables, you will need to get the appropriate values to use from the instructor.

**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**AIOPS_BASE_URL** | URL of your AAP instance to login to the AAP web console. | -------
**AIOPS_TOKEN** | Username for logging into your AAP Web console | "admin"
**AGENT_AUTH_TOKEN** | Password for logging into your AAP Web console | -------

1. Set the **default** variable values for the rows above in your `values.yaml` file:

    * `AAP_USERNAME: "admin"`
    * `AGENT_AUTH_TOKEN: "support_auth_token"`


2. Set the `AAP_ENDPOINT` variable to your **AAP UI URL** used for logging into the AAP web console. This can be retrieved from your environment details as shown below:
   
    **IMAGE**

3. Set the `AAP_PASSWORD` variable to your **AAP User Password** used for logging into the AAP web console. This can be retrieved from your environment details as shown below:
   
   **IMAGE**

4. To generate the values for the `SEND_DUMP_TRANSFER_ID` and `SEND_DUMP_TRANSFER_PASSWORD`, you must first create a new **IBM Support File Transfer ID** on ***EcuRep***. 
   
    Follow the steps below to create and record your transfer ID credentials. 

    - Create a new IBM Support File Transfer ID on ECuRep by accessing the link below:
    <a href="https://www.ecurep.ibm.com/transferids/" target="_blank">https://www.ecurep.ibm.com/transferids/</a>

    - Once authenticated, click on **+ Generate a new transfer ID**
  
        **IMAGE**
    
    - You will then be provided a **Transfer ID** and **Password**. The password will only be shown once, so make sure to **record both details in a local notepad**.

    - In your `values.yaml` file under the `env` variables section, set the value of the `SEND_DUMP_TRANSFER_ID` variable to your recorded **TransferID**, and set the value of the `SEND_DUMP_TRANSFER_PASSWORD` variable to your recorded **Transfer Password**.

Once you’ve modified the above variables for the **IBM Z Support Agent**, make sure to save your `values.yaml` file to ensure the changes get saved.

Finally, you will proceed to setting up the needed variables for the **IBM Z OMEGAMON Insights Agent**.