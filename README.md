# Kubernetes + Rancher Ansible Setup

This repository contains Ansible playbooks and roles to automate the installation of:

- A single-node Kubernetes master (using `kubeadm`)
- Calico CNI (network plugin)
- Rancher Server (deployed via Helm)
- Worker node(s) auto-join with token
- Fully modular Ansible role-based structure

---

## 📦 Features

✅ Kubernetes Master Setup  
✅ Calico CNI Installation  
✅ Rancher Server with Helm  
✅ Dynamic Worker Node Join  
✅ Role-based Playbooks  
✅ Easy One-command Execution

---

## 📁 Folder Structure

├── inventory/
│ └── hosts.ini # Inventory with master and workers
├── playbooks/
│ ├── 01-install-kubernetes.yml
│ ├── 02-install-rancher.yml
│ └── 03-join-workers.yml
├── roles/
│ ├── common/ # Common dependencies & setup
│ ├── master/ # Kubernetes master initialization
│ ├── rancher/ # Rancher via Helm
│ └── worker/ # Worker join using token
├── run-all.yml # Top-level runner
└── README.md

yaml
Copy
Edit

---

## 🚀 Quick Start

### 1. Clone the repository

```bash
git clone git@github.com:subramanya-shastry/kubernetes-rancher-ansible.git
cd kubernetes-rancher-ansible
2. Edit the inventory
Update inventory/hosts.ini with your server IPs and SSH users.

ini
Copy
Edit
[master]
k8s-master ansible_host=192.168.1.10 ansible_user=ubuntu

[workers]
k8s-worker1 ansible_host=192.168.1.11 ansible_user=ubuntu

[all:vars]
ansible_python_interpreter=/usr/bin/python3
3. Run the full setup
bash
Copy
Edit
ansible-playbook -i inventory/hosts.ini run-all.yml
Make sure you have passwordless SSH access or SSH keys configured.

🛠 Prerequisites
Ansible 2.9+ installed on control machine

Ubuntu 20.04+ nodes (master and workers)

Sudo privileges on all servers

Internet access on nodes

🔐 Access Rancher
Once the playbook completes, access Rancher UI:

cpp
Copy
Edit
http://<master-node-ip>
Login with default username and the password: admin

You can update bootstrapPassword in rancher/tasks/main.yml if needed.

📬 Contributions
Feel free to fork and enhance this repo. Pull requests are welcome!


