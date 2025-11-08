

# ansible-lab

[![CI](https://github.com/DanLinX2004X/ansible-lab/actions/workflows/pipeline.yml/badge.svg?branch=main)](https://github.com/DanLinX2004X/ansible-lab/actions/workflows/pipeline.yml)
![Ansible](https://img.shields.io/badge/Ansible-Automation-red?logo=ansible)
![YAML](https://img.shields.io/badge/YAML-Config-blue?logo=yaml)
![Ruby](https://img.shields.io/badge/Ruby-Vagrant-purple?logo=ruby)


**🇺🇸 [English Version](README.md)**

---

## Обзор проекта

ansible-lab - это учебный проект для практики с Ansible и Vagrant. Создает тестовое окружение с:

- **DB VM**: Сервер PostgreSQL базы данных
- **App VM**: Простое приложение с Python-скриптом для проверки подключения к БД и статической HTML страницей

Проект демонстрирует практические навыки работы с Ansible для собеседований на SRE/DevOps позиции, фокусируясь на автоматизации инфраструктуры и управлении конфигурациями.

> **Примечание**: Проект не использует устаревший плагин vagrant-vbguest из-за проблем с совместимостью Ruby. Provisioning полностью осуществляется через Vagrant и Ansible.

---

## Структура проекта

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

## Возможности

- **Ansible Automation**: Provisioning нескольких серверов с использованием ролей и плейбуков
- **Vagrant Infrastructure**: Управление виртуальными машинами с приватной сетью
- **CI/CD Integration**: GitHub Actions для проверки синтаксиса
- **Configuration Management**: Инфраструктура как код на YAML

## Использование

1. **Клонируйте репозиторий**:
   ```bash
   git clone https://github.com/DanLinX2004X/ansible-lab.git
   cd ansible-lab
   ```

2. **Запустите Vagrant VM**:
   ```bash
   vagrant up
   ```

3. **Проверьте синтаксис Ansible** (также проверяется в CI):
   ```bash
   ansible-playbook --syntax-check playbook.yml
   ```

4. **Проверьте подключение**:
   ```bash
   ansible all -i inventory.yml -m ping
   ```

## CI / GitHub Actions

Паipeline запускается на событиях `push` и `pull_request`:

- **Ansible playbook** - проверка синтаксиса
- **Vagrantfile** - проверка синтаксиса Ruby
- **YAML validation** (предупреждения не останавливают pipeline)

## Демонстрируемые навыки

- **Ansible**: Плейбуки, роли, управление инвентарем
- **Vagrant**: Многомашинные окружения, сетевые настройки
- **YAML**: Конфигурация как код
- **CI/CD**: Автоматизированное тестирование с GitHub Actions
- **Infrastructure Automation**: Сквозной provisioning

---

## Автор

DanLinX2004X

## Лицензия

MIT License - см. файл [LICENSE](LICENSE) для деталей.
