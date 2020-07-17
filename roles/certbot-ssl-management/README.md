CERTBOT SSL Management
=========

Install CERTBOT SSL on target host.

Role Variables
--------------

**vars/main.yml**

certbot_path: /opt/certbot
certbot_git_repo: https://github.com/certbot/certbot.git # CERTBOT github repository
certbot_challenge: dns # preferred challenge method (to validate DNS ownership)
certbot_email: myemail@email.com
certbot_domain: mydomain.com
certbot_letsencrypt: "{{ certbot_path }}/letsencrypt-auto certonly --manual --email {{ certbot_email }} --server https://acme-v02.api.letsencrypt.org/directory --agree-tos -d *.{{ certbot_domain }} --preferred-challenges={{ certbot_challenge }}"

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: target_host
      roles:
         - certbot-ssl-management
