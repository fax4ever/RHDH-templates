# 🧩 Using RHEcosystemAppEng/RHDH-templates as Golden Templates in Red Hat Developer Hub

This guide walks you through using [RHEcosystemAppEng/RHDH-templates](https://github.com/RHEcosystemAppEng/RHDH-templates) as **golden templates** inside your own instance of [Red Hat Developer Hub (RHDH)](https://redhat-developer-hub-openshift-gitops.apps.gpu.osdu.opdev.io/).

---

## ✅ Prerequisites

- Access to a running RHDH instance  
  👉 [https://redhat-developer-hub-openshift-gitops.apps.gpu.osdu.opdev.io](https://redhat-developer-hub-openshift-gitops.apps.gpu.osdu.opdev.io)
- Access to GitHub and permission to use the `RHEcosystemAppEng/RHDH-templates` repository


To use Hugging Face, a token must be securely provided. You can do this with or without Vault:

---

## 🔓 Without Vault
Manually create a Kubernetes Secret:

```bash
export HF_TOKEN=<your huggingface token>
kubectl create secret generic huggingface-secret \
  -n <your-namespace> \
  --from-literal=HF_TOKEN=$HF_TOKEN
```

Or use another secure secrets solution.

---

## 🔐 With Vault + External Secrets Operator

1. **Log in to Vault**:
   - Get the Vault route:
     ```bash
     oc get route -n vault
     ```
   - Retrieve the Vault token:
     ```bash
     oc get secret -n vault vault-token -o jsonpath="{.data.token}" | base64 --decode
     ```

2. **Manually create the secret in the Vault UI**:
   - Select the **KV** secret engine
   - Navigate to the path: `secret/janusidp`
   - On the right-hand panel, click **"Create secret"**
   - Specify the path as: `dhtemplate` (which becomes `secret/janusidp/dhtemplate`)
   - Under "Secret Data":
     - **Key**: `token`
     - **Value**: your Hugging Face token
   - Click **Save**

  **The ExternalSecret will map `token` → Kubernetes key `HF_TOKEN`**

---

## 🚀 Step-by-Step Instructions

### 1. Open the Developer Hub

Visit your RHDH instance: https://redhat-developer-hub-openshift-gitops.apps.gpu.osdu.opdev.io


---

### 2. Go to the Catalog Import Page

- From the sidebar, click **"Catalog"**
- Then click **"Register Existing Component"** (or **"Import"**)

---

### 3. Register the Golden Template Repository

Paste this URL into the import input field:

[https://github.com/RHEcosystemAppEng/RHDH-templates/blob/main/showcase-templates.yaml](https://github.com/RHEcosystemAppEng/RHDH-templates/blob/main/showcase-templates.yaml)


> 📝 This file registers all golden templates defined in the repository.

Click **"Analyze"** and then **"Import"** to complete registration.

---

### 4. Use a Template from the Create Page

- Click **"Create"** in the sidebar
- You’ll now see new golden templates like:

  - RAG Chatbot Blueprint

Click a template to launch the guided form.

---

### 5. Fill in the Form and Create a New Component

- Provide the required inputs (name, repo, owner, etc.)
- Click **"Create"**
- Once complete, follow the output links to:
  - View the source repository
  - See the component in the catalog
  - Review Argo CD
