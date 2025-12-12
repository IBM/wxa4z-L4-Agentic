# Configuring the `ptfJob` variables


Once you’ve set the values for the `env` variables in the **IBM Z Upgrade Agent** section of your `values.yaml` file, scroll down to the **`ptfJob`** variable section directly following it.

Below is a summary of each of the referenced variables within the `ptfJob` variable section.

***Note:*** *for this section, you can copy and paste each of the defaults provided below*.

**Variable name** | **Description** | **Default value to set**
--- | --- | ---
**SMPNTS** | Directory where z/OS SMP/E stores downloaded software packages | "/u/smpe"
**SMPWDIR_PATH** | Temporary workspace used during SMP/E operations - i.e. RECEIVE, APPLY, ACCEPT, Internet-based orders (RECEIVE ORDER) | "/u/smpwkdir"
**SMPJHOME** | Java SDK home directory used by SMP/E invoke Java-based services | "/usr/lpp/java/java8/J8.0_64"
**SMPCPATH** | USS path to your internet configuration file, used during RECEIVE ORDER or other SMP/E operations that require internet access | "/usr/lpp/smp/classes"
**ORDER_SERVER_URL** | URL of the IBM Enhanced Customer Center (ECC) gateway or other SMP/E order server used in RECEIVE ORDER operations | "https://eccgw01.boulder.ibm.com/services/projects/ecc/ws/"
**KEYRING** | Name of RACF keyring where the SMP/E certificate is stored | "IBMUSER/SMPERING"
**CERT_NAME** | Certificate label in keyring which is used in SMP/E operations to establish SSL/TLS secure connections | "SMPE Client Certificate"
**DOWNLOAD_METHOD** | Download method for your environment configuration. Options include https, ftp, or sftp | "https"
**DOWNLOADKEYRING** | RACF keyring used for securing outbound TLS connections, as required by z/OS | "\*AUTH\*/*"
**SIGNATUREKEYRING** | The RACF keyring that contains the public key certificate used to verify the digital signatures of PTFs. | "\*AUTH\*/*"
-----


**ACTION:** *for each of the variables in the ptfJob section referenced above, copy and paste the corresponding `Default` value into your `values.yaml` file within the **IBM Z Upgrade Agent** section.*

The result should look similar to what’s shown below:

```
ptfJob:
  SMPNTS: "/u/smpe"
  SMPWDIR_PATH: "/u/smpwkdir"
  SMPJHOME: "/usr/lpp/java/java8/J8.0_64"
  SMPCPATH: "/usr/lpp/smp/classes"
  ORDER_SERVER_URL: "https://eccgw01.boulder.ibm.com/services/projects/ecc/ws/"
  KEYRING: "IBMUSER/SMPERING"
  CERT_NAME: "SMPE Client Certificate"
  DOWNLOAD_METHOD: "https"
  DOWNLOADKEYRING: "*AUTH*/*"
  SIGNATUREKEYRING: "*AUTH*/*"
```

