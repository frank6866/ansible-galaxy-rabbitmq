Rabbitmq
========

This role is used to deploy rabbitmq. Supporting feature as follows:

* deploy rabbitmq
* create users
* delete guest user

Role Variables
--------------

If you want to add a user, you can set the following variable:

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
```

The default value of **rabbitmq_delete_guest_user** variable is False, it's recommended to delete the guest.

```
rabbitmq_delete_guest_user: True
```

Notice that you should create user by setting **rabbitmq_users** when you set **rabbitmq_delete_guest_user** to True, otherwise you could not login to rabbitmq.

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
