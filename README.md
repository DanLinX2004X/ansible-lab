# ansible-lab

[![CI](https://github.com/DanLinX2004X/ansible-lab/actions/workflows/pipeline.yml/badge.svg?branch=main)](https://github.com/DanLinX2004X/ansible-lab/actions/workflows/pipeline.yml)
![Ansible](https://img.shields.io/badge/Ansible-Automation-red?logo=ansible)
![YAML](https://img.shields.io/badge/YAML-Config-blue?logo=yaml)
![Ruby](https://img.shields.io/badge/Ruby-Vagrant-purple?logo=ruby)


**🇷🇺 [Russian Version](README.ru.md)**

---

## Project Overview

ansible-lab is a pet project to practice Ansible and Vagrant. It provisions a simple environment with:

- **DB VM**: PostgreSQL database server
- **App VM**: Simple application environment with Python script for DB connectivity check and static HTML page

This project demonstrates practical Ansible skills for SRE/DevOps interviews, focusing on infrastructure automation and configuration management.

> **Note**: The project does not use the outdated vagrant-vbguest plugin due to Ruby compatibility issues. Provisioning is handled fully via Vagrant and Ansible.

---

## Project Structure

```
ansible-lab/
├── ansible.cfg
├── .gitattributes
├── .gitignore
├── .github/workflows/pipeline.yml
├── inventory.yml
├── ping.yml
├── playbook.yml
├── README.md
├── roles/
│   ├── app/
│   │   ├── files/index.html
│   │   ├── tasks/main.yml
│   │   └── templates/check_db.py.j2
│   └── db/
│       └── tasks/main.yml
├── .vagrant/
│   ├── machines/
│   │   ├── app/virtualbox/vagrant_cwd
│   │   └── db/virtualbox/vagrant_cwd
│   └── rgloader/loader.rb
└── Vagrantfile
```

---

## Features

- **Ansible Automation**: Multi-server provisioning using roles and playbooks
- **Vagrant Infrastructure**: VM management with private networking
- **CI/CD Integration**: GitHub Actions for syntax validation
- **Configuration Management**: YAML-based infrastructure as code

## Usage

1. **Clone the repository**:
   ```bash
   git clone https://github.com/DanLinX2004X/ansible-lab.git
   cd ansible-lab
   ```

2. **Start Vagrant VMs**:
   ```bash
   vagrant up
   ```

3. **Check Ansible syntax** (CI also covers this):
   ```bash
   ansible-playbook --syntax-check playbook.yml
   ```

4. **Verify connectivity**:
   ```bash
   ansible all -i inventory.yml -m ping
   ```

## CI / GitHub Actions

Pipeline triggers on `push` and `pull_request` events:

- **Ansible playbook** syntax check
- **Vagrantfile** Ruby syntax check  
- **YAML validation** (warnings don't fail pipeline)

## Skills Demonstrated

- **Ansible**: Playbooks, roles, inventory management
- **Vagrant**: Multi-VM environments, networking
- **YAML**: Configuration as code
- **CI/CD**: Automated testing with GitHub Actions
- **Infrastructure Automation**: End-to-end provisioning

---

## Author

DanLinX2004X

## License

MIT License - [LICENSE](LICENSE) check for details
