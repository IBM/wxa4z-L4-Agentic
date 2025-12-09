# Summary of **IBM Z Upgrade Agent** capabilities

The **IBM Z Upgrade Agent** enables system programmers to perform z/OS upgrades through the watsonx Assistant for Z chat interface. It provides precise responses by leveraging z/OSMF APIs and client-specific documentation stored in the zRAG.

Below is a summary of the agent capabilities.

**Agent capbility** | **Description**
--- | ---
**List software products** | Provides a comprehensive list of software products for a given system
**List software instance details** | Shows detailed metadata of a given software instance such as its Name, Description, Global Zone, Target Zone, and so on
**Retrieve missing FIXCATs by software instance Retrieve missing FIXCATs by software product** | Identifies missing FXCAT Updates for specific software instances and systems.
**Acquire missing FIXCAT updates** | Retrieves the required PTFs for the specified RESOLVERS or FIXCAT names.
**Monitor PTF Acquisition status** | Tracks the progress and current status of background jobs initiated to acquire PTFs.
**Install the acquired PTFs** | Begins the installation or update process for the requested PTFs.
**Retrieve the installation or update status** | Retrieves the status of installation or update processes using either the process ID or the names of the software instance and system.
**Display HOLD data** | Shows HOLD data related to any unresolved HOLDS.
**Resume installation or update process** | Continues the installation or update process if the user agrees to resolve all unresolved HOLDS.
**Cancel the installation or update process** | Cancels the installation or update process only upon user request.
**Check hardware-compatibility for upgrade** | Performs a check if the given system's hardware is compatible for an upgrade to a specified version
**Retrieve content from agent documentation stored in zRAG** | Answers the upgrade workflow-related queries using the ingested docs for the agent.


