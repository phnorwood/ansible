DNS Management
=========

Install and configure DNS (BIND) server for immediate use, excluding DNS records.

Role Variables
--------------
**[defaults/main.yml]**  
dns_packages: { bind, bind-utils  }  
dns_service: named  
dns_firewall_services: dns  

**Variables available in [vars/main.yml]**  
*// dns domain*  
dns_suffix: mydomain.com  

*// interface (receiving DNS requests)*  
dns_ipv4_interface: 10.0.0.5  

*// host octet for DNS interface*  
dns_reverse_octet: 5  

*// DNS network address*  
dns_cidr: 10.0.0.0/24  

*// forward zone name*  
dns_forward_zone: "{{ dns_suffix }}"  
dns_forward_zone_file: "forward.{{ dns_suffix }}"  
dns_reverse_zone: "0.0.10.in-addr.arpa"  
dns_reverse_zone_file: "reverse.{{ dns_suffix }}"  
dns_hostname: mydnshostname  

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------
```
- hosts: target_host
  roles:
     - dns-management
```
