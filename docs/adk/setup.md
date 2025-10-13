# Installing and setting up your ADK environment

In this section you will install the **ADK** to your local workstation and configure your environment with your watsonx Orchestrate instance.

1. To set up your local ADK environment, you will need the **`orchestrate`** command-line utility. If you already have this installed you can skip to the next step. 
   
    To verify whether you have it installed, run the following command from your local command-line or Terminal window:

    `orchestrate --version`

    ***If you do not have it installed, follow the instructions below:***

    **a.** First, make sure you have **Python 3.11** or later installed on your local workstation. To check your current Python version, open up a terminal or command-prompt and run the following command:

    ```
    python --version
    ```

    !!! Warning "**If you have an older version...**"

        If you have an older version of Python installed, follow these steps to install a newer version:

        - **MacOS users**: <a href="https://developer.watson-orchestrate.ibm.com/getting_started/installing#macos" target="_blank">https://developer.watson-orchestrate.ibm.com/getting_started/installing#macos</a>
        - **Windows users**: <a href="https://developer.watson-orchestrate.ibm.com/getting_started/installing#windows" target="_blank">https://developer.watson-orchestrate.ibm.com/getting_started/installing#windows</a>
  

    **b.** Once **Python 3.11** is installed, you can install the ADK by running the following command in your local command-line or Terminal:

    ```
    pip install --upgrade ibm-watsonx-orchestrate
    ```

    **c.** Verify it's installed by running the following command:

    ```
    orchestrate --version
    ```

2. Next, configure your **watsonx Orchestrate** environment in the ADK by firstly locating the values of your **Service Instance URL** and **IBM Cloud API key**. This is the environment where you will deploy your custom agent.
   
    !!! Warning "**Where to find these values?**"

        If you don't already have these values recorded, you can find your watsonx Orchestrate **Service Instance URL** by following the instructions in Section ***[Retrieve watsonx Orchestrate Service Instance URL](../watsonx-ai/service-instance-url.md)***.

        Your **IBM Cloud API key** can be found by following the instructions in Section ***[Generate IBM Cloud API key](../watsonx-ai/api-key.md)***.

3. Once you have your values for your **watsonx Orchestrate Service Instance URL** and **IBM Cloud API key**, ***activate your environment*** within the ADK. This can be done by running the following command in your local command-prompt or terminal window, replacing `<env name>` with any name you want to reference as your WxO environment, and replacing `<your Service Instance URL>` with your unique Service Instance URL from the preceding step:
   
    ```
    orchestrate env add -n <env name> -u <your Service Instance URL> --type ibm_iam --activate
    ```

4. After issuing the above command, you will be prompted for your ***WXO API key*** as shown below:
   
    **IMAGE**

    **Copy and paste** the value of your **IBM Cloud API key** from the preceding steps and hit **enter**. You should then see that your environment is now active, as shown below:

    **IMAGE**

5. Once activated, verify you’re successfully connected by running the following command to view existing agents in your environment:
   
    ```
    orchestrate agents list
    ```

For more details on the above process, see the **<a href="https://developer.watson-orchestrate.ibm.com/getting_started/installing" target="_blank">official ADK Developer Guide</a>**.
