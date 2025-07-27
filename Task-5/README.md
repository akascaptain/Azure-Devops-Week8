# Azure DevOps: Creating a Linux/Windows Self-Hosted Agent

## Overview

Self-hosted agents in Azure DevOps provide flexibility by allowing you to run your pipelines on your own machines — whether Linux or Windows — giving you control over the environment, tools, and configurations used during builds and deployments.

This guide walks through setting up a self-hosted agent on both Linux and Windows platforms.

## Objectives

- Understand the purpose and benefits of self-hosted agents.
- Set up and configure an Azure DevOps agent on Linux.
- Set up and configure an Azure DevOps agent on Windows.
- Register the agent with your Azure DevOps organization.
- Run and verify pipeline jobs using the self-hosted agent.

## Prerequisites

- A physical or virtual machine running a supported version of Linux or Windows.
- Administrative or root access to the machine.
- Internet connectivity from the agent machine to Azure DevOps.
- An Azure DevOps organization and project.
- Permissions to create or manage agent pools.

## Creating a Self-Hosted Agent

### Step 1: Create or Choose an Agent Pool

1. Navigate to **Project Settings > Agent Pools** in your Azure DevOps project.
2. Create a new agent pool or choose an existing one (e.g., `SelfHostedPool`).

### Step 2: Download and Configure the Agent

#### Linux Agent Setup

1. SSH into your Linux machine.
2. Install prerequisites (example for Ubuntu):

   ```bash
   sudo apt-get update
   sudo apt-get install -y libssl-dev libcurl4 openssh-client unzip
   ```

3. Create a directory for the agent and download the latest package:

   ```bash
   mkdir myagent && cd myagent
   curl -O https://vstsagentpackage.azureedge.net/agent/3.236.1/vsts-agent-linux-x64-3.236.1.tar.gz
   tar zxvf vsts-agent-linux-x64-3.236.1.tar.gz
   ```

4. Configure the agent:

   ```bash
   ./config.sh
   ```

   Provide:
   - Azure DevOps URL (e.g., `https://dev.azure.com/yourorganization`)
   - Personal Access Token (PAT)
   - Agent pool name
   - Agent name
   - Work folder (default `_work`)

5. Install and start the agent as a service:

   ```bash
   sudo ./svc.sh install
   sudo ./svc.sh start
   ```

#### Windows Agent Setup

1. Download the Windows agent from:

   [https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/windows-agent](https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/windows-agent)

2. Extract the zip file to a directory (e.g., `C:\agent`).

3. Open Command Prompt as Administrator, navigate to the agent directory:

   ```cmd
   cd C:\agent
   config.cmd
   ```

4. Enter the details when prompted:
   - Azure DevOps URL
   - Personal Access Token (PAT)
   - Agent pool name
   - Agent name
   - Work folder (default `_work`)

5. Install and start the agent service:

   ```cmd
   .\svc install
   .\svc start
   ```

### Step 3: Verify the Agent

- In Azure DevOps, go to **Project Settings > Agent Pools**.
- Select your agent pool to see the new agent status. It should be **online** and **idle**.
- Use this agent in your pipeline YAML by specifying:

  ```yaml
  pool:
    name: SelfHostedPool
  ```

## Best Practices

- Run agents with minimal required permissions.
- Secure the machine and network hosting the agent.
- Regularly update the agent to the latest version.
- Use agent tags to manage workloads efficiently.
- Monitor agent health and logs for troubleshooting.

## Resources

- [Linux Agent Setup - Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/linux-agent?view=azure-devops&tabs=IP-V4)
- [Windows Agent Setup - Microsoft Docs](https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/windows-agent?view=azure-devops)
- [Azure DevOps Agents Video Tutorial](https://www.youtube.com/watch?v=Cu7zx9u1sOE)

## Author

**Akash Shinde**  
B.Tech CSE (Data Science), R. C. Patel Institute of Technology  
CSI ID: **CT_CSI_DV_4920**  
Email: **221106045@rcpit.ac.in**

