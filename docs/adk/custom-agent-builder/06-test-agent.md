# Test the IPL Validator Agent

In this section, you will access your imported agent within your watsonx Orchestrate environment and test the agent’s execution flow. The scenario follows the following flow below, and the agent uses its two available tools to validate that your zOS system's configuration and subsystems are what you'd expect after an IPL.

1. When the user prompts the agent to `run IPL check` or `validate my IPL` or something similar, the agent will kick off the first step in the **Instructions** section of your agent definition:
   
    ```
    STEP 1. check to make sure you are on the right IPL pack. run your Issue an operator command from the system console tool using the command "D IPLINFO".  Extract the value inside CURRENT IPL DEVICE from the response.
    Print out the full output. Format the response prettily.
    STOP AND WAIT FOR THE OUTPUT TO BE FULLY FORMATTED PRETTILY AND PRINTED TO THE USER 
    ```

    This will call the `sendOperatorCommand` tool, passing `D IPLINFO` as the command input. Note that the agent will finish executing each step in the flow before returning the results back to the user. 

    The output of this step is the IPLINFO information for the user's system. 

2. `Step 2:` the agent calls the `executeTsoCommand` tool, passing `TIME` as the command input. This will ensure that TSO is running. 

3. `Step 3:` calls the `sendOperatorCommand` tool, passing `D OMVS` as input. This verifies that OMVS is running. 

....





