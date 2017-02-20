Rabbitmq
========

Install rabbitmq.

Role Variables
--------------


```
rabbitmq_users:
  - user: openstack
    password: change_me
    vhost: /
    configure_priv: .*
    read_priv: .*
    write_priv: .*
    tags: administrator
    state: present

rabbitmq_delete_guest_user: True
```

Example Playbook
----------------

```
- hosts: rabbitmq
  become: true
  roles:
  - /path/to/rabbitmq
```

Ref
---
http://docs.ansible.com/ansible/list_of_messaging_modules.html

License
-------

MIT
