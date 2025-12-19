# Automation processing in Ubuntu-based distros

This project is a modular Ansible automation framework designed for rapid deployment and configuration of Ubuntu-based environments. Instead of writing complex tasks from scratch, you can leverage pre-built, production-ready Roles and toggle features using simple YAML variables. Thanks to ansible roles that allow you configr your own setup.

## Keys

- Choose only the components you need (Docker, PHP, MariaDB, etc.)
- Built-in support for Nginx acting as a frontend proxy for Apache.
- No need to edit tasks; configure your entire server via group_vars/vars.yml or in your playbook.
- Includes a `common` role for baseline server hardening and updates.
- Easy to add new roles for different CMS or database types.
- Automate configure wordpress.

## Examples

1. Install docker
```yml
---
hosts: servers
become: true
roles:
  - docker
```

2. Install php versioning and apache mod
```yml
---
hosts: servers
become: true
vars:
  php_version: "8.4"
  ioncube: true # Install ioncube extension
  apache: true
roles:
  - php
  - webserver
```

3. Install webservers and make nginx proxy for apache
```yml
---
hosts: servers
become: true
vars:
  nginx: true
  apache: true
  apache_port: 8080 # default is also 8080, but we explicit here for example
  nginx_proxy_apache: true
roles:
  - webserver
```
