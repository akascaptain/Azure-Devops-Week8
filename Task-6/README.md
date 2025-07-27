# Configuring Pre and Post-Deployment Approvals in Azure DevOps Release Pipelines

## Introduction

This guide provides step-by-step instructions on how to implement **pre-deployment** and **post-deployment** approval workflows in Azure DevOps Release Pipelines. These approval gates help ensure controlled and secure deployments by requiring manual verification by designated stakeholders before or after a deployment stage.

## Key Features

- Manual intervention checkpoints before and after deployment.
- Assignment of one or multiple approvers.
- Timeout and rejection handling for approvals.
- Integration with both classic release pipelines and YAML-based environments.

## Setup Instructions

### Classic Release Pipeline Method

1. Open your Azure DevOps project and navigate to **Pipelines > Releases**.
2. Select or create a release pipeline.
3. Click on the desired **environment**.
4. Locate and click the **Pre-deployment conditions** icon.
5. Add the list of users or groups as approvers before deployment.
6. Repeat the same for **Post-deployment conditions** if post-deployment approval is required.
7. Configure timeouts and other settings as needed.
8. Save the pipeline.

### YAML Pipeline with Environments

1. Go to **Pipelines > Environments** in Azure DevOps.
2. Create or select an existing environment.
3. Under **Approvals and checks**, add approvers.
4. In your pipeline YAML, reference this environment:

```yaml
stages:
- stage: Deploy
  jobs:
  - deployment: DeployJob
    environment: 'Staging'
    strategy:
      runOnce:
        deploy:
          steps:
          - script: echo "Deploying application..."
```

Deployments will pause awaiting approval when targeting the configured environment.

## Best Practices

- Clearly communicate approval responsibilities to stakeholders.
- Use groups for approvers to simplify management.
- Regularly review and update approval configurations.
- Leverage notifications to ensure timely approvals.

## References

- Official Documentation: [Azure DevOps Approvals and Checks](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/approvals/?view=azure-devops&tabs=yaml)
- Video Guide: [Azure DevOps Test Plans & Approvals](https://www.youtube.com/watch?v=Cu7zx9u1sOE)

---

### Author Details

**Akash Sinde**  
B.Tech CSE (Data Science), R. C. Patel Institute of Technology  
CSI ID: **CT_CSI_DV_4920**  
Email: **221106045@rcpit.ac.in**

