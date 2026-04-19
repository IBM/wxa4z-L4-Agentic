# Deploying the Token Exchange service for PassTicket generation


# Overview


# Steps 

## Setup 

### Transfering mtls package to z/OS Unix

### Configure passticket support

- AG UGROUP OMVS(GID(0) SHARED)

- SETROPTS CLASSACT(PTKTDATA) RACLIST(PTKTDATA) GENERIC(PTKTDATA)
- SETROPTS CLASSACT(IDIDMAP) RACLIST(IDIDMAP) GENERIC(IDIDMAP)
- SETROPTS CLASSACT(IDIDMAP) RACLIST(IDIDMAP) GENERIC(IDIDMAP)
- RDEFINE PTKTDATA IRRPTAUTH.IZUDFLT.* UACC(NONE) OWNER(UGROUP)
- RDEFINE PTKTDATA IZUDFLT SSIGNON(KEYMASKED(4D494B4547495A55)) APPLDATA('NO REPLAY PROTECTION')
- PERMIT IRRPTAUTH.IZUDFLT.* CL(PTKTDATA) ID(UGROUP) ACCESS(UPDATE)
- PERMIT IRRPTAUTH.IZUDFLT.* CL(PTKTDATA) ID(IBMUSER) ACCESS(UPDATE)
- SETROPTS RACLIST(PTKTDATA) REFRESH                                   
- SETROPTS RACLIST(IDIDMAP) REFRESH                                    
- SET IKJTSO=00

### Add Passticket user

- "AU {{ new_userid }} DFLTGRP(UGROUP) TSO(ACCTNUM(*) PROC(IZUFPROC) SIZE(2096128))"
- "PW USER({{ new_userid }}) NOINTERVAL"
- "ALU {{ new_userid }} PASSWORD(temppass) OMVS(UID(0) SHARED)"
- "CO ({{ new_userid }}) GROUP(IZUADMIN)"
- "CO ({{ new_userid }}) GROUP(CFZADMGP)"
- RACMAP ID({{ new_userid }}) MAP USERDIDFILTER(NAME('{{ new_email }}')) REGISTRY(NAME('LDAPS://BLUEPAGES.IBM.COM')) WITHLABEL('{{ new_userid }} ON BLUEPAGES')
- SETROPTS RACLIST(IDIDMAP) REFRESH


### Start the Token Exchange Service

- RALTER FACILITY BPX.NEXT.USER APPLDATA('0/0')
- SETROPTS RACLIST(FACILITY) REFRESH           
- ADDGROUP AUTTGRP OMVS(AUTOGID) DATA('WXA4Z GROUP')
- ADDUSER AUTTUSER NOPASSWORD DFLTGRP(AUTTGRP) OMVS(HOME(/tmp) PROGRAM(/bin/sh) AUTOUID) NAME('WXA4Z USER') DATA('WXA4Z Token Exchange Server')    
- RDEFINE STARTED AUTTKNST.* STDATA(USER(AUTTUSER) GROUP(AUTTGRP) TRUSTED(NO)) DATA('WXA4Z Token Exchange Server') 
- SETROPTS RACLIST(STARTED) REFRESH

### In USS:


- export JAVA_HOME=/usr/lpp/java/java17/J17.0_64
- export PATH=$JAVA_HOME/bin:$PATH
- export JAVA_DIR=/usr/lpp/java/java17/J17.0_64
- export PATH=$JAVA_DIR/bin:$PATH

- nohup java -jar token-exchange-mtls.jar


## Optional Testing:

### Step 1: Register the agent:

curl --request PUT \
  --url https://wxa4z-authorization-route-wxa4z-zad.apps.wxa4z-cpd522-x86-medium-dev.cp.fyre.ibm.com/api/v1/agents/wxa4z:cics:agent \
  --header 'Authorization: !cicsagent@' \
  --header 'Content-Type: application/json' \
  --header 'User-Agent: insomnia/11.4.0' \
  --data '{ 	"service_endpoint":"https://tolec78.vmec.svl.ibm.com:5443" }'


### Step 2: Get Token

curl --request GET \
  --url https://wxa4z-authorization-route-wxa4z-zad.apps.wxa4z-cpd522-x86-medium-dev.cp.fyre.ibm.com/api/v1/agents/wxa4z:cics:agent/token \
  --header 'Authorization: !cicsagent@' \
  --header 'accept: application/json' 

### Step 3: Get Passticket


curl --request POST \
  --url https://wxa4z-authorization-route-wxa4z-zad.apps.wxa4z-cpd522-x86-medium-dev.cp.fyre.ibm.com/api/v1/agents/wxa4z:cics:agent/passticket \
  --header 'Authorization: Bearer <replace token>' \
  --header 'Content-Type: application/json' \
  --header 'accept: application/json' \
  --data '{   "applid": "<APPLID>",   "emailid": "<EMAIL_ID>" }'
