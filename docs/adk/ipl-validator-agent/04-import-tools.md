# Importing tools 

Tools are essential components of agents, enabling them to perform actions such as querying data, creating documents, or executing jobs on behalf of user. Tools often require a connection to work properly, i.e. in the case of z/OSMF where the tools must authenticate before calling an API.

With the ADK, tools can be created either using OpenAPI specifications, or by using Python scripts. This section will be focused on using Python tools.

In this scenario, your ***IPL Validator Agent*** will be leveraging 2 different tools:


- ***sendOperatorCommand***
    
    This is a Python defined tool that allows the agent to issue MVS operator commands via z/OSMF Console API. The agent will be able to execute any operator command and receive synchronous command responses. Some examples of how it can be used include:

    - D A,L - Display active address spaces
    - D U,DASD - Display DASD usage
    - D IPLINFO - Display IPL information
    - D M=CPU - Display CPU configuration
    - F jobname,command - Modify job command


- ***executeTsoCommand***

    Another python defined tools that allows the agent to execute TSO commands via z/OSMF TSO/E Address Space Services API. The agent will be able to execute TSO commands on z/OS and retrieve the corresponding output from z/OS. Some examples of how it can be used include:        
    
    - TIME - Display current time and date
    - LISTDS - List dataset information
    - LISTCAT - List catalog entries
    - ALLOCATE - Allocate datasets
    - DELETE - Delete datasets
    - RENAME - Rename datasets
    - SEND - Send messages to users
    - PROFILE - Display or modify TSO profile


In this section, you will import the tool files within your workspace to create your agent tools for later use. For more details on creating tools, see <a href="https://developer.watson-orchestrate.ibm.com/tools/overview" target="_blank">here</a>.

1. Within VS Code, click on the `list_cert_tool.json` file under the ‘Tools’ sub-folder to view the contents.
   
    ![](_attachments/tools1.png)

2. Scroll to the bottom of the file and replace `<AAP UI URL>` with the **AAP UI URL** of your own environment (*paste it within the double-quotes*). It should look similar to the following:
   
    ![](_attachments/tools2.png)

    *Make sure to save the file before moving on*

3. Next, open up the `renew_cert_tool.json` file under the ‘Tools’ sub-folder to view the contents.
   
   

4. Just as before, scroll to the bottom of the file and replace `<AAP UI URL>` with the **AAP UI URL** of your own environment (within double-quotes).
   
    *Again, make sure to save the file before moving on.*

5. Import the first OpenAPI tool from the `list_cert_tool.json` file by running the following command from your VS Code Terminal command-prompt:
   
    ```
    orchestrate tools import -k openapi -f Tools/list_cert_tool.json --app-id ansible
    ```

6. After issuing the command, you should see a message similar to what’s shown below:
   
    ![](_attachments/tools4.png)

    This indicates that your `get_cert` tool was imported successfully.

7. Next, import the second OpenAPI tool from the `renew_cert_tool.json` file by running the following
command:

    ```
    orchestrate tools import -k openapi -f Tools/renew_cert_tool.json --app-id ansible
    ```

1. After issuing the command, you should get a message indicating that your `renew_cert` tool was imported successfully:
   
    ![](_attachments/tools5.png)

2. Finally, you will import the Python tool from the `job_output_status_tool.py` file. 
    
    To do this, copy and paste the following command into your VS Code Terminal command-prompt and click enter.

    ```
    orchestrate tools import -k python -f Tools/job_output_status_tool.py --app-id ansible
    ```

3.  Once you’ve successfully imported all 3 tools, verify they’re now active by running the following command:
    
    ```
    orchestrate tools list
    ```

    This should output a table similar to below showing all your imported tools.

    ![](_attachments/tools6.png)
