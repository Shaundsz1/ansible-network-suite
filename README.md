# Ansible Network Automation Suite

A professional multi-platform network automation project using Ansible to manage
Cisco IOS XE and NX-OS devices. Built to demonstrate real-world network automation
skills including configuration management, VLAN provisioning, and automated auditing.

---

## 🔧 What This Project Does

- **Pushes standardized configurations** to Cisco Cat8000v (IOS XE) devices
- **Manages VLANs** on Cisco Nexus 9000 (NX-OS) switches
- **Audits device state** across both platforms simultaneously
- **Generates automated reports** with device facts, versions, and VLAN status
- Built using **Ansible Roles** — the industry-standard project structure

---

## 🖥️ Platforms Tested

| Device | Platform | OS |
|---|---|---|
| Cisco Catalyst 8000v | IOS XE | 17.15.04c |
| Cisco Nexus 9000 | NX-OS | 10.3(8) |

Tested against **Cisco DevNet Always-On Sandboxes** — real hardware, no simulations.

---

## 📁 Project Structure
```
ansible-network-suite/
├── ansible.cfg                    # Ansible configuration
├── inventory/
│   └── hosts.ini                  # Device inventory (not committed)
├── group_vars/
│   └── all.yml                    # Global variables - single source of truth
├── playbooks/
│   ├── site.yml                   # Master playbook using Roles
│   ├── vlans.yml                  # Standalone VLAN management
│   └── audit.yml                  # Multi-device audit + report generation
└── roles/
    ├── base_config/               # IOS XE configuration role
    │   ├── tasks/main.yml
    │   └── defaults/main.yml
    └── vlan_manager/              # NX-OS VLAN management role
        ├── tasks/main.yml
        └── defaults/main.yml
```

---

## ⚡ Key Concepts Demonstrated

- **Idempotency** — Playbooks can run repeatedly, only changing what needs changing
- **Variables-driven design** — All config values live in `group_vars/all.yml`
- **Ansible Roles** — Modular, reusable, enterprise-standard structure
- **Multi-platform automation** — Single project managing IOS XE and NX-OS
- **Automated reporting** — Audit results written to file with timestamp

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Ansible

### Installation
```bash
git clone https://github.com/Shaundsz1/ansible-network-suite.git
cd ansible-network-suite
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
ansible-galaxy collection install cisco.ios cisco.nxos
```

### Usage
```bash
# Run full configuration suite
ansible-playbook playbooks/site.yml -i inventory/hosts.ini

# VLAN management only
ansible-playbook playbooks/vlans.yml -i inventory/hosts.ini

# Generate audit report
ansible-playbook playbooks/audit.yml -i inventory/hosts.ini
```

---

## 📊 Sample Audit Report Output
```
============================================
 NETWORK AUDIT REPORT
 Generated: 2026-02-26  20:34:25
============================================

[Cisco Cat8000v]
 Hostname   : Ansible-Managed-Device
 IOS Version: 17.15.04c
 Model      : C8000V
 Interfaces : GigabitEthernet1, GigabitEthernet2, GigabitEthernet3

[Cisco Nexus 9000]
 Hostname   : nexus
 NX-OS Ver  : 10.3(8)
 Model      : Nexus9000 C9300v Chassis
 Active VLANs: 10, 20, 30, 40
============================================
```

---

## 🛠️ Built With

- [Ansible](https://www.ansible.com/) - Automation platform
- [Cisco IOS Collection](https://galaxy.ansible.com/cisco/ios) - IOS XE modules
- [Cisco NX-OS Collection](https://galaxy.ansible.com/cisco/nxos) - NX-OS modules
- [Cisco DevNet Sandbox](https://devnetsandbox.cisco.com/) - Test environment