# 🔧 SimLab-2 Ansible Roles

Welcome to **SimLab-2** – a set of modular and reusable Ansible roles for automating your Simlab environment! 🚀  
Each role under the `Roles/` directory is designed to configure and manage specific aspects of your lab systems.

---

## 📦 Available Roles

### 🧰 `common` – Base Configuration
Handles essential system setup:

- 🆙 Updates package lists and upgrades packages
- 🧪 Installs common utilities (like `vim`, `curl`, `git`)
- 📜 Configures a custom Message of the Day (MOTD)
- ⏰ Sets up time synchronization

Use this on **all** lab machines as the first step in provisioning.

---

### 🔥 `firewall` – Host-Based Firewall Setup
Configures system-level firewalls using **iptables** (Linux) or **PF** (BSD):

- 🔒 Sets default deny-all policy
- 🟢 Allows host-specific TCP/UDP ports via Jinja2 templates
- 📝 Supports logging and ICMP control
- 🧩 Uses `allowed_ports_by_host` variable for flexible rule creation

Example:
```yaml

allowed_ports_by_host:
  server1: ["22/tcp", "80/tcp", "443/tcp"]
  server2: ["22/tcp", "3306/tcp"]

Customizable via variables in your playbook.

▶️ Example Playbook

- name: Common config for all servers
  hosts: all
  become: yes
  roles:
    - common

- name: Secure the servers
  hosts: all
  become: yes
  roles:
    - firewall


ansible-playbook firewall.yaml -i hosts_inventory OR ansible-playbook common.yaml -i hosts_inventory

✅ Requirements
🐍 Python installed on target machines

🔑 SSH access to all hosts

🧑‍💻 Ansible 2.16+ on control node

🖥️ Supported OS: Ubuntu/Debian/RedHat/

🔐 Sudo privileges

📝 License
Licensed under the MIT License. Free to use, modify, and share!

👤 Author
Louai Al-Obaidi


