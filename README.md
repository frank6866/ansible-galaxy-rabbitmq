Rabbitmq
=======

Install rabbitmq.

Role Variables
--------------

```
rabbitmq_user:
  - user: frank
    password: change_me
    vhost: /
    configure_priv: .*
    read_priv: .*
    write_priv: .*
    tags: administrator
    state: present

delete_guest_user: True
```

Example Playbook
----------------

```
- hosts: rabbitmq
  become: true
  roles:
  - frank6866.rabbitmq
```

Ref
---
http://docs.ansible.com/ansible/list_of_messaging_modules.html

License
-------

MIT
