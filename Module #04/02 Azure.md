# Azure

## What is Microsoft Azure?

Microsoft Azure is a cloud computing platform and service created by Microsoft. It provides a wide range of tools and services to build, deploy, and manage applications through Microsoft's global network of data centers.

Whether you're hosting a simple website, running a full-scale enterprise app, or training AI models — Azure has you covered.

There are 5 key concepts in Azure --

1. Microsoft Entra ID
   Microsoft Entra ID is Azure’s cloud-based identity and access management (IAM) service. It’s what handles login, user management, permissions, and access control for all your Azure services and Microsoft apps.

   > 💡 Think of it as the central gatekeeper of your Azure environment.

   - Manages users, groups, roles, and enterprise applications
   - Supports SSO (Single Sign-On), MFA (Multi-Factor Authentication), and RBAC (Role-Based Access Control)
   - Powers identity for services like Microsoft 365, Azure, GitHub Enterprise, and more

2. Directory (Tenant)
   A Directory, also called a tenant, is a dedicated instance of Microsoft Entra ID. When you create an Azure account, a directory is created for you.

   > 💡 If Microsoft Entra ID is the entire identity system, then your Directory (Tenant) is your organization’s private office inside it — where you control all user identities, access, and apps.

   - Every user, group, and app lives inside a directory
   - One Microsoft account can be associated with multiple directories

3. Subscription
   A Subscription is a billing container in Azure. It links your usage to a payment method and determines how much you’re charged.

   > 💡 It’s where your actual resources live — like VMs, databases, and web apps.

   - One directory can have multiple subscriptions
   - You can apply different policies, budgets, and access control at the subscription level
   - Ideal for organizing dev/test/prod environments separately

4. Resource Group
   A Resource Group is a logical container for related Azure resources.

   > 💡 Think of it like a folder for organizing services that share a common lifecycle (e.g., a web app and its database).

   - Helps with organizing, managing, and deleting resources as a unit
   - Useful for access control, monitoring, and cost tracking

5. Azure Regions & Availability Zones
   - Region: A geographic area (e.g., Central India, East US) where Azure has data centers
   - Availability Zones: Separate physical locations within a region, offering high availability and fault tolerance

| **Concept**        | **What it is**                     | **Analogy**                   |
| ------------------ | ---------------------------------- | ----------------------------- |
| Microsoft Entra ID | Identity & access system           | Security gatekeeper           |
| Directory (Tenant) | Your organization’s identity space | Main office building          |
| Subscription       | Billing + resource container       | Project budget and tracker    |
| Resource Group     | Logical group of resources         | Folder for related services   |
| Region/Zone        | Where your data lives              | Data center location + backup |

Along with this, there are two other important concepts to learn about a CI/CD pipeline (more on CI/CD later).

1. Azure Container Registry (ACR)  
   Azure Container Registry is a private Docker registry hosted in Azure.

   It allows you to store, manage, and secure Docker container images (and Helm charts, OCI artifacts, etc.) in your own Azure environment — instead of using public registries like Docker Hub.

   > 💡 Think of ACR as your organization's private app store for containers.

2. Azure Container Apps (ACA)
   Azure Container Apps is a serverless container platform — it lets you run containerized apps without managing servers or infrastructure.

   You just deploy your container, and Azure takes care of scaling, networking, and runtime — automatically.

   > 💡 Think of Azure Container Apps as a run-anywhere engine — perfect for deploying modern apps fast, without worrying about Kubernetes complexity.

---

Reference: [Azure's Official Documentation](https://learn.microsoft.com/en-us/azure/?product=popular)
