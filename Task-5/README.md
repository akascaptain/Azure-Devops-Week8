
````
# Azure DevOps Pipelines: Creating a Linux/Windows Self-Hosted Agent

## Overview
This repository provides a detailed guide to setting up a **self-hosted agent** (Linux or Windows) for Azure DevOps Pipelines. A self-hosted agent is a machine you configure to run CI/CD jobs from your pipelines, giving you complete control over the environment, software, and hardware resources.

---

## Objectives
- Understand what a self-hosted agent is and why it is used.
- Install and configure a self-hosted agent on **Linux** or **Windows**.
- Connect the agent to an Azure DevOps organization.
- Run pipelines using the self-hosted agent.

---

## Prerequisites
- An **Azure DevOps Organization** and **Project**.
- Administrative privileges on the machine where the agent will be installed.
- A supported OS:
  - **Windows**: Windows 10/11 or Windows Server 2016/2019/2022.
  - **Linux**: Ubuntu, CentOS, RHEL, or Debian.
- **.NET Core 6+** installed (for Linux agents).
- A personal access token (PAT) from Azure DevOps with required scopes:
  - **Agent Pools (Read & manage)**.
  - **Deployment Groups (Read & manage)** (if applicable).

---

## Steps to Create a Self-Hosted Agent

### Step 1: Create a Personal Access Token (PAT)
1. Go to your Azure DevOps organization.
2. Navigate to **User settings > Personal access tokens**.
3. Click **+ New Token**.
4. Add scopes: **Agent Pools (Read & Manage)**.
5. Save and copy the token (you will need it later).

---

### Step 2: Create an Agent Pool
1. Navigate to **Organization settings > Agent Pools**.
2. Click **Add pool**.
3. Provide a name (e.g., `SelfHostedPool`) and save.

---

### Step 3: Download the Agent Package
1. Go to **Project Settings > Agent pools**.
2. Select the newly created pool.
3. Click **New Agent**.
4. Choose **Windows** or **Linux** and download the agent package.

---

## Windows Self-Hosted Agent Setup

### Step 4: Extract and Configure
1. Extract the agent package (e.g., `C:\agent`).
2. Open **Command Prompt** or **PowerShell** and run:
   ```powershell
   cd C:\agent
   .\config.cmd
````

3. Provide:

   * Azure DevOps server URL (e.g., `https://dev.azure.com/your-org`).
   * PAT token.
   * Agent pool name (`SelfHostedPool`).
   * Agent name (e.g., `win-agent-01`).
   * Work folder (default: `_work`).

### Step 5: Run the Agent

* Start the agent interactively:

  ```powershell
  .\run.cmd
  ```
* To run as a Windows Service:

  ```powershell
  .\svc install
  .\svc start
  ```

---

## Linux Self-Hosted Agent Setup

### Step 4: Extract and Configure

1. Extract the package:

   ```bash
   tar zxvf vsts-agent-linux-x64-*.tar.gz
   cd ./vsts-agent-linux-x64-*
   ```
2. Run configuration:

   ```bash
   ./config.sh
   ```
3. Provide:

   * Azure DevOps server URL (e.g., `https://dev.azure.com/your-org`).
   * PAT token.
   * Agent pool name (`SelfHostedPool`).
   * Agent name (e.g., `linux-agent-01`).
   * Work folder (default: `_work`).

### Step 5: Run the Agent

* Start the agent interactively:

  ```bash
  ./run.sh
  ```
* Install and start as a service:

  ```bash
  sudo ./svc.sh install
  sudo ./svc.sh start
  ```

---

## Verify the Agent

* Go to **Project Settings > Agent pools > SelfHostedPool**.
* Check if your agent status is **Online**.

---

## Usage in Pipelines

Reference the self-hosted agent in your YAML pipeline:

```yaml
trigger:
- main

pool:
  name: SelfHostedPool

steps:
- script: echo "Running on self-hosted agent"
```

---

## Best Practices

* Keep the machine updated with necessary build and deployment tools.
* Run the agent as a dedicated service account with least privileges.
* Use separate agents for different environments (Dev, Test, Prod).
* Regularly update the agent software to the latest version.
* Monitor the agent logs and health for failures.

---

## Resources

* [Set up a Linux self-hosted agent (Microsoft Docs)](https://learn.microsoft.com/en-us/azure/devops/pipelines/agents/linux-agent?view=azure-devops&tabs=IP-V4)
* [Video: Azure DevOps Test Plans & Agents](https://www.youtube.com/watch?v=Cu7zx9u1sOE)

---

## Author

**Akash Shinde**
B.Tech CSE (Data Science), R. C. Patel Institute of Technology
CSI ID: **CT\_CSI\_DV\_4920**
Email: **[221106045@rcpit.ac.in]**


