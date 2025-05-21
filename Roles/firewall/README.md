# 🧰 Ansible Role: common

This role handles basic setup tasks that are commonly needed on all lab systems.

---

## ✅ What It Does

- 🆙 Updates the package cache
- 📦 Installs essential packages
- 📜 Configures a custom Message of the Day (MOTD)

---

## ⚙️ Role Variables

| Variable               | Description                                | Default         |
|------------------------|--------------------------------------------|-----------------|
| `common_packages`      | List of packages to install                | `[]`            |
| `common_configure_motd`| Enable or disable custom MOTD              | `true`          |
| `common_motd_message`  | Message to display in `/etc/motd`          | `"Welcome!"`    |

---

## 🚀 Example Playbook

```yaml
- name: Apply common base configuration
  hosts: all
  become: yes
  roles:
    - role: common
      vars:
        common_packages:
          - htop
          - curl
          - tree
        common_motd_message: |
          Welcome to the SimLab environment!
          Managed by Ansible 🤖
📄 License
MIT

👤 Author
Created by Louai Al-Obaidi
Part of the SimLab-2 project 🚀

