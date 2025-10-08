# Install the `oc` CLI and log into OpenShift

### Install the `oc` command-line utility
The Red Hat OpenShift command line interface (CLI) utility, which is known as `oc`, must be installed on your local workstation. If you already installed the `oc` utility, you can proceed to the next section.

This can be verified by issuing the `oc` command on your local command-line. If you already installed the `oc` utility, you can proceed to the next section.

1. Log into your ***Single Node OpenShift*** cluster via web console by **`following the instructions in.....`**
   
   
2. Click the **Help** icon and then click **Command Line Tools**.
   
    **IMAGE**

3. Click the link under **oc - OpenShift Command Line Interface (CLI)** for the operating system of your local machine.
   
    **IMAGE**

    Clicking the preceding link automatically downloads either a **.zip** or **.tar** file specific to your operating system. Extract the file's content.

    Place the **oc** binary for your operating system (OS) in a directory that is in your default `PATH`, or set the `PATH` environment variable to include the location of the **oc** binary.

4. Verify the installation by running the `oc` command on your local workstation. 

    `oc --help`

    **IMAGE**

### Log into your OpenShift cluster from your local terminal

**Note:** If you just installed the `oc` utility, you should already be logged into the cluster and can skip the first couple of steps.

1. Log into your ***Single Node OpenShift*** cluster via web console by **`following the instructions in.....`**

2. Click the `kube:admin` profile drop-down and click **Copy login command**.
   
    **IMAGE**

3. Click **Display Token**.
   
    **IMAGE**

4. Select and copy the ***Log in with this token*** string.

    *For most operating systems, double-click the value, then right-click and select **Copy***.

    **IMAGE**

5. Open a command prompt or terminal window on your local workstation. Then paste the login command and press **enter**.
   
    **IMAGE**

### Download the *zAssistantDeploy* configuration folder

In this step you will download a **.zip** file from Box containing the YAML files needed to deploy **zAssistDeploy**.

1. On your local workstation, click on this Box link to view the provided **zAssistDeploy.zip** file:
   
    <a href="https://ibm.box.com/s/idllzje6oqiy02fv4zodubn1m78szp5s" target="_blank">https://ibm.box.com/s/idllzje6oqiy02fv4zodubn1m78szp5s</a>

2. Once you can view the file in Box, click **Download** to download the file to your local workstation.
   
    **IMAGE**

3. Once downloaded, go to your local workstation’s Downloads folder and extract/unzip the zAssistDeploy.zip file.

4. You should then see the unzipped/extracted folder with the included YAML files as shown below (for Mac users):
   
    **IMAGE**

5. On your local machine’s command-line, change to the ***zAssistDeploy*** directory. On Mac, this can be done by issuing the following command:
   
    `cd Downloads/zAssistDeploy`

    *Use the corresponding command for Windows users.*

6. Once you’ve changed to the extracted ***zAssistDeploy*** directory via command-line, you should be able to list the contained files. Below is an example for Mac users:
   
    **IMAGE**

