CERTBOT SSL Management
=========

Install CERTBOT on target host. Role output will also include explicit instructions on next steps to generate customer SSL certificates for target domain.

e.g.

```

```


Role Variables
--------------

**vars/main.yml**

certbot_path: /opt/certbot

certbot_git_repo: https://github.com/certbot/certbot.git

certbot_challenge: dns

certbot_email: myemail@email.com

certbot_domain: mydomain.com

certbot_letsencrypt: "{{ certbot_path }}/letsencrypt-auto certonly --manual --email {{ certbot_email }} --server https://acme-v02.api.letsencrypt.org/directory --agree-tos -d *.{{ certbot_domain }} --preferred-challenges={{ certbot_challenge }}"

Example Playbook
----------------

    - hosts: target_host
      roles:
         - certbot-ssl-management
