# Configuring your Db2 Agent with Db2 connections

Now that you've successfully deployed your Db2 for z/OS Agent, you must configure it which involves a few manual steps covered in this section.

### Enabling your Db2 subsystems on Wazi aaS to use the non-default ports

-import the AAP template and Launch it 

### Mount the Db2 license file

As a pre-req for using the Db2 for z/OS Agent, it must have ODBC connectivity enabled. Server-side verification is recommended, however, client-side verification is supported by mounting the license into the deployed container at `/usr/local/lib64/python3.12/site-packages/clidriver/license`. 

*NOTE:* missing licenes files at the above location will lead to a licensing error when later creating a connection to Db2 via MCP server REST API endpoint. 

Follow the below instructions to mount the license in the deployed agent pod...



### Bind the ODBC DBRMs to Db2 subsystems

Prior to setting an agent connection to your Db2 subsystems, you must also bind some required packages on your Db2 subsystems. Follow the below steps:

1. Access Db2 Agent pod

2. Navigate/cd to `$IBM_DB_HOME/bin`

3. Run the command below to bind the packages on the **DBD1** Db2 subsystem, replacing the following values with your own unique values:

    - `<host>`: public IP of your Wazi aaS
    - `<password>`: the RACF passphrase you set for your IBMUSER ID


    ```
    ./db2cli bind $IBM_DB_HOME/bnd/@db2cli.lst -database DBD1LOC:<host>:8100 -user IBMUSER -passwd "<password>"
    ```

4. Run the command below to bind the packages on the **DBC1** Db2 subsystem, replacing the following values with your own unique values:

    - `<host>`: public IP of your Wazi aaS
    - `<password>`: the RACF passphrase you set for your IBMUSER ID


    ```
    ./db2cli bind $IBM_DB_HOME/bnd/@db2cli.lst -database DBC1LOC:<host>:8000 -user IBMUSER -passwd "<password>"
    ```


### Creating Db2 connections


https://www.ibm.com/docs/en/db2-for-zos/13.0.0?topic=configuring-connecting-agent-db2



curl -X POST -H "Content-Type: application/json" -d '{"alias": "DBD1", "host": "52.118.252.194", "port": "8100", "connection_uri": "db2+ibm_db://IBMUSER:MY @52.118.252.194:8100/DBD1LOC", "appl_id": "IZUDFLT", "username": "IBMUSER", "password": "MY", "location": "DBD1LOC"}' https://db2z-mcp-route-wxa4z-zad.apps.692f98c265861.am1.techzone.ibm.com/api/v1/databases/connections

curl https://db2z-mcp-route-wxa4z-zad.apps.692f98c2658a61.am1.techzone.ibm.com/api/v1/databases/connections