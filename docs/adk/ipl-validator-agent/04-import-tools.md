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

1. Within VS Code, click on the `sendOperatorCommand.py` file. Take some time to review the contents. 

    Specifically, note the following section:

    ```
    get_status_url = urljoin(base_url, f'restconsoles/consoles/defcn')
    
    request_body = {
        "cmd": cmd,
        "sol-key": "JES"
    }
    ```

    The resulting z/OSMF API endpoint that will get called in this tool is:
    
    `https://<public-ip>:10443/zosmf/restconsoles/consoles/defcn`

    Within the body of the API call, `cmd` gets passed as input from the agent. Depending on the step in the IPL validation, the agent may pass `D A,L` as the command to execute, as an example. 
   
    Then click on the `executeTsoCommand` file and take time to review its content as well. 

2. Import the `sendOperatorCommand` tool by running the following command from your VS Code Terminal command-prompt:
   
    ```
    orchestrate tools import -k python -f tsoPython.py --app-id zosmf 
    ```

    After issuing the command, you should see a message similar to what's shown below:

    That indicates that the `sendOperatorCommand` tool was imported successfully. 

3. Similarly, import the `executeTsoCommand` tool by running the following command:
   
    ```
    orchestrate tools import -k python -f operatorPython.py --app-id zosmf
    ```

    Confirm that this tool was also imported successfully. 



4.  Once you’ve successfully imported both tools, verify they’re now active by running the following command:
    
    ```
    orchestrate tools list
    ```

    This should output a table similar to below showing all your imported tools.

    ![](_attachments/tools6.png)
