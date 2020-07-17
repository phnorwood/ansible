DNS Management
=========

Install and configure DNS (BIND) server for immediate use, excluding DNS records. DNS records can then be added to the deployed server.

Role Variables
--------------
**[defaults/main.yml]**  
dns_packages: { bind, bind-utils  }  
dns_service: named  
dns_firewall_services: dns  

**[vars/main.yml]**  
*dns domain*
    dns_suffix: mydomain.com
dns_ipv4_interface: 10.0.0.5 *## ipv4 interface receiving dns requests*  
dns_reverse_octet: 5 *## ipv4 dns host octet*  
dns_cidr: 10.0.0.0/24 *## ipv4 cidr network notation (allow queries to dns server)  
dns_forward_zone: "{{ dns_suffix }}" *## forward zone name  
dns_forward_zone_file: "forward.{{ dns_suffix }}" *## forward zone file  
dns_reverse_zone: "0.0.10.in-addr.arpa" *## reverse zone name  
dns_reverse_zone_file: "reverse.{{ dns_suffix }}" *## reverse zone file  
dns_hostname: mydnshostname *## dns server hostname  

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
