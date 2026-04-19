# Optional

## Create/configure new z/OSMF certificate

- RACDCERT GENCERT ID(IZUSVR) SUBJECTSDN( CN('your.zos.system.com') O('IBM') OU('IZUDFLT') ) ALTNAME( DOMAIN('your.zos.system.com') ) NOTAFTER(DATE(2030-12-31)) WITHLABEL('DefaultzOSMFCert.SAN') KEYUSAGE(HANDSHAKE DATAENCRYPT CERTSIGN)

  - replace your.zos.system.com with the `xxx.techzone.ibm.com` DN of your system

- RACDCERT ID(IZUSVR) CONNECT( LABEL('DefaultzOSMFCert.SAN') RING(ZOSMF_RING) DEFAULT)

- Restart z/OSMF IZUSVR1 started task


## Upload new z/OSMF certificate to cert secret

Once z/OSMF comes back up, do the following:

- export SITE="your.zos.system.com"
  
- openssl s_client -connect ${SITE}:10443 -servername ${SITE} -showcerts </dev/null \
 | awk '/-----BEGIN CERTIFICATE-----/,/-----END CERTIFICATE-----/{print $0}' > ${SITE}_full_chain.pem

- Copy the outputted .pem file to local keyboard
- Paste it into the `service-endpoint-cert-secret` secret and save it
- Restart the MCP pod deployment


