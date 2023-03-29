## Ansible role for [Nginx Proxy Manager v2.9.19](https://github.com/NginxProxyManager/nginx-proxy-manager/tree/v2.9.19).
a simple way to add a new proxy host via ansible playbook.
Checked for version v2.9.19.

Description
-----------
module: nginx-proxy-manager-ansible
description: a simple way to add a new proxy host or to delete via ansible playbook

Requirements
------------

This role requires Ansible 2.7 or higher, Docker and Docker-Compose.

Change and update a [docker-compose.yml](https://github.com/DenAV/nginx-proxy-manager-ansible/blob/main/docker/docker-compose_npm.yml) file. Bring up your stack by running docker-compose, further info [here](https://github.com/DenAV/nginx-proxy-manager-ansible/tree/main/docker).

Role Variables
--------------

- `npm_api_url` - IP for the Nginx Proxy Manager REST API. Default to `http://192.168.1.5:81/api`.
- `npm_user` - User to authenticate the Nginx Proxy Manager REST API.
- `npm_password` - Password to authenticate the Nginx Proxy Manager REST API.
- `npm_access_token` - Tokens are required to authenticate against the API.

- `npm_api_domain_name` - Domain Names are required to create the Proxy host.
- `npm_api_host` - Forward Hostname / IP are required to create the Proxy host.
- `npm_api_ssl_forced` - Is SSL Forced? Default is `False`.
- `npm_api_create_host` - IWhether to create (present), or no a proxy host. Default is `False`.

See the [`defaults/main.yml`](https://github.com/DenAV/nginx-proxy-manager-ansible/blob/main/roles/npm-management/defaults/main.yml) or [`vars/*.yml`](https://github.com/DenAV/nginx-proxy-manager-ansible/tree/main/roles/npm-management/vars) file listing all possible options which you can be passed to a runner registration command.

Example Playbook
----------------

```yaml
- name: NPM - create proxy host
  hosts: localhost
  gather_facts: no

  roles:
    - role: npm-management
      npm_api_domain_name: "site-2.example.com"
      npm_api_host: "172.16.1.2"
      npm_api_ssl_forced: True
      npm_api_create_host: True

```
