# Locate your WML Base URL

The last shared secret needed to configure for your agents deployment is the `<WATSONX_ML_URL>` configuration parameter. 

This corresponds to the Base URL of your IBM watsonx.ai Runtime API endpoint. Follow the instructions below to locate and record the value for your environment.

1. Assuming you’re still accessing the IBM Cloud account where your ***watsonx Orchestrate Trial/Standard Plan*** environment was accessed, navigate back to the **Resource list** within the Cloud console.
   
   **IMAGE**

2. Under the **AI / Machine Learning** resource drop-down, identify the **Location** associated with your services as shown below:
   
    **IMAGE**

    ***NOTE:** in the example above, the services are available in the **us-south** region. The region for your environment may be different.*
   
    **Take note of your services’ region.**

3. The URL value of your `<WATSONX_ML_URL>` variable will be one of the following URLs depending on the region of your services. Copy and paste the appropriate URL for your region and copy to a notepad, labeled as `<WATSONX_ML_URL>`. This will be used later on for the agents deployments.
   
    - **us-south**
      - `https://us-south.ml.cloud.ibm.com`
    - **eu-gb**
      - `https://eu-gb.ml.cloud.ibm.com`
    - **eu-de**
      - `https://eu-de.ml.cloud.ibm.com`
    - **jp-tok**
      - `https://jp-tok.ml.cloud.ibm.com`
    - **au-syd**
      - `https://au-syd.ml.cloud.ibm.com`
    - **ca-tor**
      - `https://ca-tor.ml.cloud.ibm.com`
  

    Reference the latest list of WML Endpoint URLs [here](https://cloud.ibm.com/apidocs/machine-learning#endpoint-url).

