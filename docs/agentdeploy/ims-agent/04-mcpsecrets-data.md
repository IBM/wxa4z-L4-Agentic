# Configuring the `mcpSecrets.data` variables

```
mcpSecrets:
  data:
    SERVICE_ENDPOINT: "https://itzvsi-550000kksb-907dyw9w.techzone.ibm.com:5444"
    ZOSMF_ENDPOINT: "https://itzvsi-550ksb-907dyw9w.techzone.ibm.com:10443/zosmf"
    AGENT_AUTH_TOKEN: "AGENT_AUTH_TOKEN"
```

1. Set the `SERVICE_ENDPOINT` variable. 
   
    The `SERVICE_ENDPOINT` variable defines the URL or network address where z/OSMF services are exposed, but uses a different port where mTLS authentication is set. 

    Follow the below steps to locate and record the `SERVICE_ENDPOINT` URL for your **zD&T** instance. 

    a. Locate your instance's `HOSTNAME` in environemnt details


    b. In the below URL, replace `<hostname>` with the unique hostname for your **zD&T** environment: 

    ```
    https://<hostname>.techzone.ibm.com:5444
    ```

    c. Copy and paste the resulting string for the `SERVICE_ENDPOINT` variable in your `values.yaml` file. 


2. Set the `ZOSMF_ENDPOINT` variable.

    The `ZOSMF_ENDPOINT` variable is the URL for accessing your **zD&T** instance's z/OSMF services.

    Similar to the previous step, replace `<hostname>` with the unique hostname for your **zD&T** environment:

    ```
    https://<hostname>.techzone.ibm.com:10443/zosmf
    ```

    Then copy and paste the resulting sttring for the `ZOSMF_ENDPOINT` variable in your `values.yaml` file. 



3. Set the `AGENT_AUTH_TOKEN` variable. 
