# Day 4 – Ansible Configuration Management

This document explains the fundamentals of Ansible and demonstrates how it is used for configuration management and automation. The focus is on understanding Ansible architecture, inventory, ad-hoc commands, and playbooks for managing remote servers.

---

## 📘 Introduction

Ansible is an open-source automation tool used for:

- Configuration Management  
- Application Deployment  
- Infrastructure Provisioning  
- Orchestration  

It works over SSH and does not require agents on managed nodes, making it lightweight and easy to adopt.

Ansible follows a **push-based model**, where commands and configurations are pushed from the control node to managed nodes.

---

## 🏗 Architecture Overview

Ansible consists of:

### 1. Control Node  
The machine where Ansible is installed and executed.

### 2. Managed Nodes  
Remote servers controlled by Ansible (via SSH).

### 3. Inventory  
A file that lists target servers.

### 4. Modules  
Reusable units of work (package install, file copy, service restart, etc.).

### 5. Playbooks  
YAML files that define automation tasks.

---

## ⚙️ Environment Used

- Ubuntu (Ansible Control Node)
- Remote Ubuntu servers (Managed Nodes)
- SSH connectivity
- GitHub (for project storage)

---

## 📦 Installing Ansible

Update system packages:

```bash
sudo apt update
Install Ansible:

sudo apt install ansible -y
Verify installation:

ansible --version
📁 Inventory Configuration
Create inventory file:

nano inventory
Example:

[web]
192.168.64.130

[db]
192.168.64.131
Test connectivity:

ansible all -i inventory -m ping
Successful ping confirms SSH connectivity.

⚡ Ad-Hoc Commands
Check uptime:

ansible all -i inventory -a "uptime"
Install nginx:

ansible web -i inventory -b -m apt -a "name=nginx state=present"
Start nginx:

ansible web -i inventory -b -m service -a "name=nginx state=started"
These commands show how Ansible executes tasks remotely without playbooks.

📜 Creating Ansible Playbook
Create playbook:

nano setup.yml
Example:

---
- hosts: web
  become: true
  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present

    - name: Start nginx
      service:
        name: nginx
        state: started
Run playbook:

ansible-playbook -i inventory setup.yml
This automates installation and startup of nginx on all web servers.

🌐 Accessing Application
After playbook execution, open browser:

http://<server-ip>
Nginx default page confirms successful deployment.

🧠 Key Concepts Learned
1️⃣ Agentless Architecture
No software needed on managed nodes.

2️⃣ Idempotency
Running playbooks multiple times does not break systems.

3️⃣ Inventory Management
Centralized host configuration.

4️⃣ YAML Playbooks
Human-readable automation.

5️⃣ SSH-Based Communication
Secure remote execution.

🔄 Typical Workflow
Ansible Control Node
        ↓
Inventory
        ↓
Playbook
        ↓
Managed Nodes
✅ Outcome
By completing Day 4:

Installed and configured Ansible

Connected multiple remote servers

Executed ad-hoc commands

Created Ansible playbooks

Automated nginx deployment

Accessed deployed service via browser

This demonstrated how infrastructure tasks can be automated consistently across servers.
