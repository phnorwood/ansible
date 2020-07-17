CERTBOT SSL Management
=========

Install [CERTBOT](https://certbot.eff.org/) on target host for the purpose of generating wildcard SSL cert (*.mydomain.com).

End result is a target host configured with CERTBOT, including explicit instructions (command) to generate custom SSL certificates for the target domain.

The following is an example execution of the role output.

e.g.

```
[root@proxy ~]# /opt/certbot/letsencrypt-auto certonly --manual --email myemail@email.com --server https://acme-v02.api.letsencrypt.org/directory --agree-tos -d *.mydomain.com --preferred-challenges=dns
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator manual, Installer None
Obtaining a new certificate
Performing the following challenges:
dns-01 challenge for mydomain.com

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
NOTE: The IP of this machine will be publicly logged as having requested this
certificate. If you're running certbot in manual mode on a machine that is not
your server, please ensure you're okay with that.

Are you OK with your IP being logged?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: Y

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Please deploy a DNS TXT record under the name
_acme-challenge.mydomain.com with the following value:

05fgBfcvsaoJ40JDS4XraGEiolHQykdlCWOEmKpzfqs

Before continuing, verify the record is deployed.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Press Enter to Continue
Waiting for verification...
Cleaning up challenges

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/mydomain.com/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/mydomain.com/privkey.pem
   Your cert will expire on 2020-10-15. To obtain a new or tweaked
   version of this certificate in the future, simply run
   letsencrypt-auto again. To non-interactively renew *all* of your
   certificates, run "letsencrypt-auto renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le

[root@proxy ~]# 
```

Role Variables
--------------

**[defaults/main.yml]**  

```
# install path for certbot
certbot_path: /opt/certbot
# certbot github repo
certbot_git_repo: https://github.com/certbot/certbot.git
```

**[vars/main.yml]**  

```
# [challenge method](https://certbot.eff.org/docs/challenges.html) for certbot
certbot_challenge: dns
# email
certbot_email: myemail@email.com
# domain
certbot_domain: mydomain.com
# formatted output commaned (to be executed at role completion)
certbot_letsencrypt: "{{ certbot_path }}/letsencrypt-auto certonly --manual --email {{ certbot_email }} --server https://acme-v02.api.letsencrypt.org/directory --agree-tos -d *.{{ certbot_domain }} --preferred-challenges={{ certbot_challenge }}"
```

Example Playbook
----------------

    - hosts: target_host
      roles:
         - certbot-ssl-management
