# ansible-role-lets-encrypt [![Build Status](https://travis-ci.org/shengyou/ansible-role-lets-encrypt.svg?branch=master)](https://travis-ci.org/shengyou/ansible-role-lets-encrypt)

安裝 Lets Encrypt

* Ubuntu 14.04, 16.04
* CentOS 6, 7

Requirements
------------

* ansible >= 2.4
* python >= 2.6

Role Variables
--------------

```

web_service: nginx
# 可設置 nginx 或 apache，預設為 nginx
```

以下為非必要，只有當你希望能一併註冊憑證時才須設置。

```
certbot_certs:
  - email: example@example.com
    domains:
     - example1.com
     - example2.com
  - email: example2@example.com
    domains:
     - example3.com

certbot_auto_renew: true
# 預設為 true，會自動在 cron 中增加 renew 的 job
```

Dependencies
------------

none.

Example Playbook
----------------

```
- hosts: your_host
  gather_facts: yes
  become: yes

  vars:
    certbot_certs:
      - email: example@example.com
        domains:
         - example1.com

  roles:
    - ansible-role-lets-encrypt
```

License
-------

MIT
