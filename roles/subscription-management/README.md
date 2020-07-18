Role Name
=========

Execute **subscription-manager register --auto-attach** against remote host.

Assumed registering to Red Hat CDN (using auto-attach).

Role Variables
--------------

**vars/rhn-info.yml**
```
# username (for Red Hat Account)
rhn_user_name: myuser
# password (for Red Hat Account)
rhn_user_password: mypassword
```

Dependencies
----------------
Some considerations need to be taken when implenenting this role.

1. Variable file [vars/rhn-info.yml](https://github.com/phnorwood/ansible/blob/master/roles/subscription-management/vars/rhn-info.yml) should be encrypted once populated (using ansible-vault) to secure confidential information.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: target_host
      roles:
         - subscription-management
