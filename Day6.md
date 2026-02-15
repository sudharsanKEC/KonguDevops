



# Ansible Configuration Management

## 1. Introduction
Ansible is an open-source automation tool used for configuration management, application deployment, and task automation. It allows you to manage IT infrastructure quickly and efficiently.

## 2. Architecture Overview
Ansible operates in a distributed architecture. The system includes a control node and managed nodes. The control node is where Ansible is installed and commands are executed, while managed nodes are the servers that Ansible controls.

## 3. Environment Used
The following environment has been used for this configuration management lesson:
- OS: Ubuntu 20.04
- Ansible Version: 2.10

## 4. Installing Ansible
### Ubuntu
To install Ansible on Ubuntu, run the following commands:
```bash
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

### CentOS
For CentOS, use:
```bash
sudo yum install epel-release
sudo yum install ansible
```

## 5. Inventory Configuration
Ansible manages machines via an inventory file, which can be a static or dynamic file.
Example of a static inventory file (`/etc/ansible/hosts`):  
```
[web]
192.168.1.10
192.168.1.11

[db]
192.168.1.20
```

## 6. Ad-Hoc Commands
Ad-Hoc commands allow you to manage your servers quickly. Here are some examples:
```bash
ansible all -m ping
ansible web -m apt -a "name=apache2 state=latest"
```

## 7. Creating Ansible Playbook
A playbook is a YAML file containing a series of tasks to be executed. Here is an example playbook:
```yaml
- hosts: web
  tasks:
    - name: Install Apache
      apt:
        name: apache2
        state: latest
```

## 8. Accessing Application
Once the playbook has been executed, you can access the application by navigating to `http://<server_ip>` in your web browser.

## 9. Key Concepts Learned
- Understanding of playbooks, modules, and inventory files.
- How to use Ad-Hoc commands effectively.

## 10. Typical Workflow
1. Define inventory
2. Write playbooks
3. Execute playbooks with Ansible
4. Verify the results

## 11. Outcome
By following these practices, you can efficiently manage your server configurations, reduce deployment errors, and improve operational efficiency.






