
# 📊 Azure DevOps: Configuring Dashboards and Work Item Queries

This document provides a concise and practical guide to **configure dashboards and create work item queries** in **Azure DevOps** for tracking progress, visualizing data, and improving collaboration.

---

## 🔍 Work Item Queries

Queries in Azure DevOps allow you to filter, find, and organize work items based on conditions.

### ✅ Query Types

* **Flat List**: Displays a simple list of work items.
* **Tree of Work Items**: Shows parent-child hierarchy (e.g., Epics > Features > Stories).
* **Direct Links**: Displays linked work items based on specific relationships.

### 🛠️ Creating a Query

1. Go to **Boards** → **Queries**.
2. Select **New Query**.
3. Set filters such as:

   * `Work Item Type = Bug`
   * `Assigned To = @Me`
   * `Iteration Path = @CurrentIteration`
4. Adjust columns, sorting, and grouping.
5. Save your query (Personal or Shared).

---

## 📈 Dashboards

Azure DevOps Dashboards allow you to monitor project progress with real-time widgets and reports.

### 📋 Steps to Configure a Dashboard

1. Navigate to your Project → **Overview** → **Dashboards**.
2. Create a new dashboard or edit an existing one.
3. Click **+ Add Widget**, examples include:

   * **Query Tile**: Displays a count of query results.
   * **Chart for Work Items**: Visualizes a saved query.
   * **Sprint Burndown**, **Velocity**, **Test Results**, etc.
4. Configure widget settings:

   * Link to a query.
   * Set refresh intervals.
   * Choose display format (e.g., pie chart, bar graph).

### 🔒 Permissions

* Only users with edit rights can modify dashboards.
* Widget visibility respects query access permissions.

---

## 📌 Example Use Case

**Goal**: Track all open bugs in the current sprint.

1. Create a **Flat List** query:

   ```txt
   Work Item Type = Bug AND
   State != Closed AND
   Iteration Path = @CurrentIteration
   ```
2. Save it as a **Shared Query**.
3. Add widgets:

   * A **Query Tile** to display total open bugs.
   * A **Pie Chart** to show bug distribution by severity.

---

## ✅ Key Benefits

* Centralized and real-time reporting.
* Improved visibility and transparency.
* Helps in sprint planning and reviews.
* Enhanced collaboration between team members and stakeholders.

---

## 📚 Additional Resources

* [Using Queries in Azure DevOps (Microsoft Docs)](https://learn.microsoft.com/en-us/azure/devops/boards/queries/using-queries?view=azure-devops&tabs=browser)
* [Azure DevOps Dashboards Overview](https://learn.microsoft.com/en-us/azure/devops/report/dashboards/overview?view=azure-devops)
* [YouTube Tutorial: Azure DevOps Pipelines and Dashboards](https://www.youtube.com/watch?v=xH5EY7FCFQw)

---

## 👤 Author

**Akash Shinde**
CSI ID: `CT_CSI_DV_4920`
Azure Account: `221106045.@rcpit.ac.in`
