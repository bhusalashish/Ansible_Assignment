# 🚀 Ansible Assignment - 202 🎯

This repository contains the **code and demo** for the **Ansible Assignment - 202**, showcasing an automated web server deployment using **Ansible** on AWS **EC2 instances**. 🖥️☁️

## 📝 Problem Statement

Configure two VMs (**VM1** and **VM2**) either on your own hardware or in a cloud environment. Use **Ansible** to deploy a **web server** on both VMs running on **port 8080** with a web page that displays:

-  **"Hello World from VM-1"** on **VM1**
-  **"Hello World from VM-2"** on **VM2**

Include **Ansible tasks** for **deployment and cleanup**. Submit a **Word document** with screenshots, a demo, and all **Ansible code/scripts** via GitHub. 📸📜

## 🔥 Steps to Follow

### 1️⃣ Launch AWS EC2 Instances 🌐
- Create **three EC2 instances**:
  - 🖥️ **Ansible Control Node** (to run Ansible)
  - 🌍 **VM1 & VM2** (to deploy web servers)
- Configure **inbound rules** for **VM1 & VM2**:
  - ✅ Allow **HTTP traffic on port 80**
  - ✅ Enable **SSH access** as needed

### 2️⃣ Set Up SSH Access 🔑
- Log into each **EC2 instance**.
- On the **Ansible control node**, add the **private key**:
  ```sh
  mkdir -p ~/.ssh && chmod 700 ~/.ssh
  echo "PRIVATE_KEY_CONTENT" > ~/.ssh/ansible_key
  chmod 600 ~/.ssh/ansible_key
  ```

### 3️⃣ Configure Ansible Inventory 📜
- Create an **inventory file** at `/etc/ansible/hosts`:
  ```ini
  [nodes]
  VM1_Public_IP
  VM2_Public_IP
  ```
- Set the **SSH private key path** in Ansible configuration:
  ```ini
  ansible_ssh_private_key_file=~/.ssh/ansible_key
  ```

### 4️⃣ Create and Run Ansible Playbook 🚀
- Develop an **Ansible playbook** to:
  - 📦 Install **Nginx**
  - 🔧 Change Nginx’s **default port to 8080**
  - 📝 Deploy a **custom index.html** file
  - 🔄 Restart **Nginx**
- Run the playbook:
  ```sh
  ansible-playbook deploy_nginx.yml
  ```
- ✅ **Verify** the web pages are accessible at:
  - `http://VM1_Public_IP:8080`
  - `http://VM2_Public_IP:8080`

### 5️⃣ Cleanup Playbook (Un-deploy) 🧹
- Create another **playbook** to:
  - 🛑 Stop **Nginx**
  - ❌ Uninstall **Nginx**
  - 🗑️ Remove **configuration files**
- Execute cleanup:
  ```sh
  ansible-playbook remove_nginx.yml
  ```

🎉 **Congratulations!** We've successfully automated the deployment and cleanup of a web server using Ansible! 🚀🔥
