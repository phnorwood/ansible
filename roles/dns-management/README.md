DNS Management
=========

Install and configure DNS ([BIND](https://www.isc.org/bind/)) server for immediate use, including limited DNS records for server.  

Additional DNS records can then be added to the deployed server using appropriate configuration files.

Role Variables
--------------
**defaults/main.yml**  

```
dns_packages:
- bind
- bind-utils
dns_service: named
dns_firewall_services:
- dns
```

**vars/main.yml**  

```
# domain name
dns_suffix: mydomain.com
# primary network interface receiving dns requests
dns_ipv4_interface: 10.0.0.5
# host address octet (for reverse lookup)
dns_reverse_octet: 5
# network allowed to query dns
dns_cidr: 10.0.0.0/24
# forward lookup
dns_forward_zone: "{{ dns_suffix }}"
# forward zone file
dns_forward_zone_file: "forward.{{ dns_suffix }}"
# reverse lookup
dns_reverse_zone: "0.0.10.in-addr.arpa"
# reverze zone file
dns_reverse_zone_file: "reverse.{{ dns_suffix }}"
# dns server hostname
dns_hostname: mydnshostname
```

Example Playbook
----------------
```
- hosts: target_host
  roles:
     - dns-management
```
