# Summary of Agent Capbilities

The **IBM Z Support Agent** enables users to run Ansible playbooks through Ansible Automation Platform, triggered by user input. 

Supported playbooks include:

- **Take z/OS Dump**: Collects a dump from a specified z/OS address space
- **z/OS Send Dump**: Collects and transfers a dump from a z/OS address space to a Support Ticket

Additionally, the agent provides functionality to retrieve the status of initiated Ansible jobs and access job logs for monitoring and troubleshooting.

*Below is a summary of the agent capabilities:*

**Agent capbility** | **Description**
--- | ---
**Take z/OS dump** | Collect dump on a z/OS address space
**Send z/OS dump** | Transfer the dump collected on z/OS address space
**Retrieve job status** | Retrieve the launched ansible job status and logs

