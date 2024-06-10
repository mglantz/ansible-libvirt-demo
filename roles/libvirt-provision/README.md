Role Name
=========

A role which provisions a network and a VM on a RHEL KVM hypervisor using libvirt.

Requirements
------------

Baremetal server running RHEL and libvirt

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

https://docs.ansible.com/ansible/latest/collections/community/libvirt/index.html

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

Apache License 2.0

Author Information
------------------

Magnus Glantz, sudo@redhat.com, 2024
