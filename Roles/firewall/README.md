# 🔥 Ansible Role: firewall

This role installs and configures a firewall on RedHat and Debian-based systems, ensuring only explicitly allowed ports are open. All other traffic is blocked by default. 🔒

---

## ✅ What It Does

- 📦 Installs firewall utilities (`iptables`, `ufw`, or relevant tools)
- 🛡️ Applies a deny-all-by-default policy
- 🟢 Opens only required ports based on host-specific configuration
- ♻️ Ensures rules persist across reboots

---

## ⚙️ Role Variables

You must define which ports are allowed **per host** using the `allowed_ports_by_host` dictionary.

allowed_ports_by_host:
  server1: ["22/tcp", "80/tcp"]
  server2: ["22/tcp", "3306/tcp"]
Each entry must follow the format: "PORT/PROTOCOL" (e.g., "443/tcp" or "53/udp").

📂 Directory Structure

roles/firewall/
├── handlers/         # (optional) reload or restart firewall
├── tasks/            # install & configure firewall
├── templates/        # Jinja2 templates for rules (iptables or PF)
├── vars/             # default variables (OS-specific)
└── README.md         # you're here!
🚀 Example Playbook

- name: Configure firewall on lab servers
  hosts: all
  become: yes
  roles:
    - role: firewall
      vars:
        allowed_ports_by_host:
          "{{ inventory_hostname }}":
            - "22/tcp"
            - "80/tcp"
🧑‍💻 Requirements
Ansible 2.16+

Debian/Ubuntu or RHEL/CentOS-based systems

become: yes privileges to apply firewall rules

SSH access from control node

📄 License
MIT

👤 Author
Created by Louai Al-Obaidi
Part of the SimLab-2 project 🚀

