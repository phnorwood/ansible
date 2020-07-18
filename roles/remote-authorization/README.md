Remote Authorization
=========

Create remote user on target host, including administrator (group: wheel) privileges and SSH public key copy.

This role was created to solve the problem of first-use Ansible (e.g. how to execute Ansible from scratch if nothing yet exists on remote hosts) but can be expanded as required.

Role requires executing as **root** (or similar privileged user).

Role Variables
--------------

**vars/remote-auth-vault.yml**
```
# username
ansible_user_name: myuser
# password
ansible_user_password: mypassword
# ssh public key to copy to user profile
ansible_public_key: ssh-rsa AJHDB3NzaC1yc2EAAAADAQABAAABgQCbT4cXBgftnbSApFD5G60HsCq/hkogDI8vG6YgdunwPeBITHCu+wbgwxUZxl713LI8a6gQdgMsZPtuTZpqQUsqmUDfVXmziZ0ouz7atRyzN9FlwwrmUeo0bKQGcYBO7ObSoKSNBH+ZM1PV1XgflogsBQlgea7hvdrsx6CGop8LHU/1urKquhY+kdHNIAUwX+HxdmhsfVhsCKTjHTUmxSKuBZdZfN3CP/3EFn5hwVqohaLq8KINmV5nJHt3TfmB3NQTmMLkeZO9TSNUymC2dUart+qke5Ryu1n7MzUNwLe9lWFrMUxUCC+8w7kYfWYzl99CkXhYKlzqT45V+TgJT7mVTh5FR2bmxj/Nxfib7ViKVJq5uIKd0GXaLPfXSzkvbnb+RF9hKBrYQi0FlgeOyLNsx5aHfPGLaIU569kXd7gw23YNEll84yjyKggHfZreNECBPg4cqrWojcUesM7ltgoSWzZwONZmol0DA4ocfKrPavSB6CJAPGmC6RBRlBPRhPM= myuser@myansiblehost
```

Dependencies
------------

Some considerations need to be taken when implenenting this role.

1. Requires **root** privilege credentials, including ignoring [host key checking](https://docs.ansible.com/ansible/latest/user_guide/connection_details.html#host-key-checking) on initial connection.
1. Variable file [**vars/remote-auth-vault.yml**](https://github.com/phnorwood/ansible/blob/master/roles/remote-authorization/vars/remote-auth-vault.yml) should be encrypted once populated (using [ansible-vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html)) to secure confidential information.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: target_host
      roles:
         - remote-authorization
