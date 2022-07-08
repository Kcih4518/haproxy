# Ansible Role: HAProxy

[![CI](https://github.com/Oefenweb/ansible-haproxy/workflows/CI/badge.svg)](https://github.com/Oefenweb/ansible-haproxy/actions?query=workflow%3ACI)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-haproxy-blue.svg)](https://galaxy.ansible.com/Oefenweb/haproxy)

Installs HAProxy for kubernetes on Ubuntu Linux servers.

**Note**: This role _officially_ supports HAProxy versions 2.3.2.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    haproxy_frontend_name: 'kube-apiserver-https'
    haproxy_frontend_port: 8443
    haproxy_frontend_mode: 'tcp'

HAProxy frontend configuration directives.

    haproxy_backend_name: 'kube-apiserver-backend'
    haproxy_backend_mode: 'tcp'
    haproxy_backend_balance_method: 'roundrobin'

HAProxy backend configuration directives.

    haproxy_backend_servers:
      - name: app1
        address: 192.168.0.1:80
      - name: app2
        address: 192.168.0.2:80

A list of backend servers (name and address) to which HAProxy will distribute requests.

    haproxy_connect_timeout: 5000
    haproxy_client_timeout: 600000
    haproxy_server_timeout: 600000

A list of extra global variables to add to the global configuration section inside `haproxy.cfg`.

## Example Playbook

    - hosts: kubernetes-master
      become: true
      roles:
        - { role: kcih4518.haproxy }

## License

MIT / BSD

## Author Information

This role was created in 2022 by [Avery Yang](https://www.linkedin.com/in/avery-yang-85b554144/).
