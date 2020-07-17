Role Name
=========

Install and configure NGINX proxy server for immediate use, excluding specific proxy records.  

Subsequent proxy behaviors can be added to /etc/nginx/nginx.conf or /etc/nginx/conf.d/ as required.

Role Variables
--------------

**defaults/main.yml**  

```
nginx_packages:
- nginx
nginx_service: nginx
nginx_firewall_services:
- http
- https
```

Example Playbook
----------------

    - hosts: target_host
      roles:
         - nginx-management
