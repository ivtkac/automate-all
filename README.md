# Automation processing in Ubuntu-based distros

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
```
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
```
---
hosts: servers
become: true
vars:
  nginx: true
  apache: true
  nginx_proxy_apache: true
roles:
  - webserver
```
