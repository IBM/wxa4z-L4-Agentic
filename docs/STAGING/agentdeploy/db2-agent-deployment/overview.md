# Summary of **Db2 for z/OS Agent** capabilities

The **IBM Db2 for z/OS Agent** is an AI-powered assistant that enables you to easily obtain real-time information about your Db2 for z/OS subsystems and database objects through a simple prompt-based conversational interface. For example, you can ask it what the current value of a particular subsystem parameter is, which buffer pool a particular index uses, or if any utilities are currently running on a subsystem. In addition to providing a response, the agent also explains the method that it used to obtain the response.

Below is a summary of the agent capabilities.

**Agent capbility** | **Description**
--- | ---
**Retrieving system information** | 
Show me all the bufferpools under DBD1. | Lists all bufferpools in the specified Db2 subsystem.
Can you tell me details about BP32K? | Retrieves configuration and usage details for the specified bufferpool.
Comparing System Information Across Subsystems | Compares system information between different Db2 subsystems and shows only differences.
**Retrieving zParm Values** |
What is the zparm value of UTILITY_HISTORY in DBD1? | Shows current value of the specified zparm parameter.
**Comparing zParm Across Subsystems** | 
Show me MAXDBAT, CONDBAT, DSMAX, and APPLCOMPAT zparm values for DBD1 and DBC1. | Structured output listing the values of the requested zparm.
**Catalog Navigation with System Information** | 





### DISCLAIMER


