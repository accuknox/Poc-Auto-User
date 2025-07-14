# 🐳 Rancher User Automation via Ansible & GitHub Actions

This project automates the creation of Rancher users and assigns global roles,  
using **Ansible playbooks** triggered by a **GitHub Actions workflow**.

---

## ✅ Features
- Dynamically create new users in Rancher
- Automatically bind a user to a default global role (e.g., `user` or `admin`)
- Triggered directly from GitHub Actions UI
- Keep API tokens secure using GitHub secrets

---

## 🛠️ Prerequisites
- Rancher instance (e.g., `https://rancher.example.com`)
- Rancher **API token** with permission to create users and assign roles
- GitHub repository (this one)
- Create the following secrets in your GitHub repository:
  - `RANCHER_API_URL` → e.g., `https://rancher.example.com/v3`
  - `RANCHER_API_TOKEN` → your Rancher API token

---

## ⚙️ Usage

### 1️⃣ Trigger workflow manually
Go to your GitHub repository → **Actions** → select `Create Rancher User` workflow →  
click **Run workflow** → fill in:
- **Username** → the Rancher username to create
- **Password** → user password (⚠ must be at least 12 characters)
- **Full name** → optional, defaults to the username
- **Global role** → e.g., `user` (default) or `admin`

> 📝 Leave “Full name” blank to default to username.

---


## 🧩 How it works
- GitHub Actions workflow is triggered manually (`workflow_dispatch`)
- Workflow installs Ansible & required modules
- Runs the playbook `create_rancher_user.yml` with the provided inputs
- Ansible makes API calls to Rancher:
  - Creates the user with the given username & password
  - Assigns the specified global role to the new user

---

## 🛡️ Security notes
- Rancher API URL and API token are stored securely as GitHub secrets
- Password is passed as a workflow input (visible in Actions UI; do not use production passwords here)
- Prefer rotating API tokens regularly

---

## ✏️ Customize
- Change the default global role (`user` → `admin`) in the playbook
- Add logic to automatically bind users to specific projects or clusters
- Send notifications when users are created

---

## 🤝 Contributions
Feel free to fork, improve, and send pull requests!  
Ideas, bug reports, and enhancements are welcome.

---

## 📄 License
MIT License


