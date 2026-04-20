# Optional - Configuring your z/OSMF Certificate for the MCP container image

Currently, all MCP tools rely on z/OSMF to communicate with your z/OS system. Please note that z/OSMF console setup is required. A valid certificate is also required for secure, TLS communication.

The steps below outline how to configure a new z/OSMF certificate that enables secure access from the MCP Container image, and then providing the certificate file as a secret to the MCP server. 

## Create/configure new z/OSMF certificate

The provided commands below reference a `hostname` value, which is the unique hostname of your **zD&T** image. The value you use here should be the `Hostname` value found in your reservations, with `.techzone.ibm.com` appended to it. 

For example, ...


1. Log into your TSO session. 


2. Run the following TSO/RACF command to generate a new certificate for your z/OS system:
   
    ```
    RACDCERT GENCERT ID(IZUSVR) SUBJECTSDN( CN('<hostname>') O('IBM') OU('IZUDFLT') ) ALTNAME( DOMAIN('<hostname>') ) NOTAFTER(DATE(2030-12-31)) WITHLABEL('DefaultzOSMFCert.SAN') KEYUSAGE(HANDSHAKE DATAENCRYPT CERTSIGN)
    ```

3. Once generated, connect the newly created certificate to your z/OSMF Keyring by running the below command:

    ```
    RACDCERT ID(IZUSVR) CONNECT( LABEL('DefaultzOSMFCert.SAN') RING(ZOSMF_RING) DEFAULT)
    ```

4. Finally, restart the z/OSMF started task to take the changes by running the following Console command:
   
   `/P IZUSVR1`

   then:

   `/S IZUSVR1`


## Upload new z/OSMF certificate to cert secret

1. Once z/OSMF comes back up, do the following locally:

    ```
    export SITE="your.zos.system.com"
    ```   

    ```
    openssl s_client -connect ${SITE}:10443 -servername ${SITE} -showcerts </dev/null | awk '/-----BEGIN CERTIFICATE-----/,/-----END CERTIFICATE-----/{print $0}' > ${SITE}_full_chain.pem
    ```  


2. Copy the outputted .pem file to local keyboard


3. Paste it into the `service-endpoint-cert-secret` secret and save it


4. Restart the MCP pod deployment. 




