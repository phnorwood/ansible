# Ansible

This is a collection of Ansible playbooks and roles for general use.

Written for both entry- and professional-level users. Use cases are separated by directory.

## Requirements

Ansible is a pre-requisite for this project.

    $ sudo yum install ansible

Executed Ansible playbooks must be capable of making changes to the target hosts for success. If not yet configured, this project provides the [**remote-authorization**](https://github.com/phnorwood/ansible/tree/master/remote-authorization) role to configure Ansible remote access on target hosts.

## Using Repository

 Download or clone repository to preferred Ansible host.

```
$ git clone git@github.com:phnorwood/ansible.git
```

## Variables

The variable '*target_host*' is used throughout this project to represent the host(s) against which these playbooks and roles will execute. It must be set for successful execution and will serve the '*hosts:*' parameter.  

```
- name: playbook.yml
  hosts: "{{ target_host }}"
  ...
```
