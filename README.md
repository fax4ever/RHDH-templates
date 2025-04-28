# 🧩 Using RHEcosystemAppEng/RHDH-templates as Golden Templates in Red Hat Developer Hub

This guide walks you through using [RHEcosystemAppEng/RHDH-templates](https://github.com/RHEcosystemAppEng/RHDH-templates) as **golden templates** inside your own instance of [Red Hat Developer Hub (RHDH)](https://redhat-developer-hub-openshift-gitops.apps.gpu.osdu.opdev.io/).

---

## ✅ Prerequisites

- Access to a running RHDH instance  
  👉 [https://redhat-developer-hub-openshift-gitops.apps.gpu.osdu.opdev.io](https://redhat-developer-hub-openshift-gitops.apps.gpu.osdu.opdev.io/)
- Access to GitHub and permission to use the `[dhllamastack](https://github.com/dhllamastack)` repository

---

## 🚀 Step-by-Step Instructions

### 1. Open the Developer Hub

Visit your RHDH instance: https://redhat-developer-hub-openshift-gitops.apps.gpu.osdu.opdev.io


---

### 2. Register Golden Template(If not already registered)

- From the sidebar, click **"Catalog"**
- Then click **"Register Existing Component"** (or **"Import"**)

- Paste this URL into the import input field:

[https://github.com/RHEcosystemAppEng/RHDH-templates/blob/main/showcase-templates.yaml](https://github.com/RHEcosystemAppEng/RHDH-templates/blob/main/showcase-templates.yaml)

> 📝 This file registers all golden templates defined in the repository.

Click **"Analyze"** and then **"Import"** to complete registration.

---

### 3. Create New Software Components

- Click **"Catalog"** in the sidebar
- You’ll see All available components
- Click **"Create"** in the top right corner
- Select the template "create a rag blueprint using llamastack with vllm"
- Click "Choose"


### 4. Fill in the Form and Create a New Component

- Application information
  - Name: Name of the application
  - Description: Description of the application
  - Owner: Your GitHub username (e.g., yourgithubid)
  - Click **Next**
- Application Repository Location
  - Host Type: GitHub
  - Repository Owner: dhllamastack
  - Repository Name: (Enter the target repository name)
  - Repository Branch: main
  - Repository Server: github.com
  - CLick **Next**
- Choolse a model
  - Model: Select a model from the dropdown list
  - Hugging Face Toke: Provide your Hugging Face token
  - Enable GPU Support: Optionally check Create GPU if needed
  - CLick **Next**
- Application Namespace
  - Namespace: Enter the namespace where you want the application deployed
  - Click **Review**
- If everything looks correct, click **Create**.

- Once the creation process is complete, you can:
  - View the generated source repository
  - See the component registered in the catalog
  - Review Argo CD, CI/CD, or TechDocs integrations (if included)


