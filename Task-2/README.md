# Azure DevOps: Configuring Dashboards, Work Item Queries & Pipeline Variables

This document serves as a professional guide to **configure dashboards, create work item queries**, and **use pipeline variables** in **Azure DevOps** for improved tracking, automation, and collaboration.

---

##  Work Item Queries

Queries in Azure DevOps help filter, find, and organize work items based on defined conditions.

### Query Types

* **Flat List**: A simple list of work items.
* **Tree of Work Items**: Displays parent-child hierarchies (e.g., Epics > Features > Stories).
* **Direct Links**: Shows linked work items by relationships.

###  Creating a Query

1. Go to **Boards** → **Queries**.
2. Select **New Query**.
3. Apply filters like:

   * `Work Item Type = Bug`
   * `Assigned To = @Me`
   * `Iteration Path = @CurrentIteration`
4. Customize columns, sorting, and grouping.
5. Save the query as **Personal** or **Shared**.

---

##  Dashboards

Azure DevOps Dashboards visualize real-time project data through widgets and charts.

###  Steps to Configure a Dashboard

1. Navigate to **Project** → **Overview** → **Dashboards**.
2. Create a new dashboard or edit an existing one.
3. Click **+ Add Widget**, such as:

   * **Query Tile**: Displays query result counts.
   * **Chart for Work Items**: Visualizes query data.
   * **Sprint Burndown**, **Velocity**, **Test Results**, etc.
4. Configure widget settings:

   * Link queries.
   * Set refresh intervals.
   * Choose display formats (e.g., pie charts or bar graphs).

###  Permissions

* Only users with appropriate rights can modify dashboards.
* Widget visibility respects query-level permissions.

---

## Using Pipeline Variables

Pipeline variables in Azure DevOps allow you to parameterize your CI/CD workflows.

###  Steps to Use Pipeline Variables

1. Navigate to **Pipelines** → **Edit Pipeline**.
2. Define variables in YAML or the classic editor:

   ```yaml
   variables:
     buildConfiguration: 'Release'
     appVersion: '1.0.0'
   ```
3. Reference variables in tasks:

   ```yaml
   steps:
   - script: echo $(buildConfiguration)
   - script: echo $(appVersion)
   ```
4. You can define **Pipeline Variables** at runtime for dynamic values.
5. Use **Variable Groups** to manage reusable variables.

### Resources

* [YouTube Tutorial: Azure DevOps Pipelines and Dashboards](https://www.youtube.com/watch?v=xH5EY7FCFQw&t=77s&pp=ygUVYXp1cmUgZGV2b3BzIHBpcGVsaW5l)
* [Microsoft Docs: Variables in Azure Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch)

---

##  Example Use Case

**Goal**: Track all open bugs in the current sprint and display pipeline build configurations.

1. Create a **Flat List** query:

   ```txt
   Work Item Type = Bug AND
   State != Closed AND
   Iteration Path = @CurrentIteration
   ```
2. Save it as a **Shared Query**.
3. Add widgets:

   * **Query Tile** to display open bug count.
   * **Pie Chart** for severity breakdown.
4. Configure pipeline variables to build in **Release** mode and display the app version.

---

##  Benefits

* Real-time visibility into work and build status.
* Centralized and customizable dashboards.
* Easier automation with parameterized pipelines.
* Better collaboration and planning.

---

##  Additional Resources

* [Using Queries in Azure DevOps](https://learn.microsoft.com/en-us/azure/devops/boards/queries/using-queries?view=azure-devops&tabs=browser)
* [Azure DevOps Dashboards Overview](https://learn.microsoft.com/en-us/azure/devops/report/dashboards/overview?view=azure-devops)
* [Pipeline Variables Documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=azure-devops&tabs=yaml%2Cbatch)
* [YouTube: Azure DevOps Pipelines & Dashboards](https://www.youtube.com/watch?v=xH5EY7FCFQw)

---

## Author

**Akash Shinde**
CSI ID: `CT_CSI_DV_4920`
Azure Account: `221106045.@rcpit.ac.in`

