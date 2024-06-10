Role Name
=========

A role which provisions a network and a VM on a RHEL KVM hypervisor using libvirt.

Requirements
------------

Baremetal server running RHEL and libvirt

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

```
# Name of base image to download
base_image_name: Fedora-Cloud-Base-Generic.x86_64-40-1.14.qcow2

# Full url to download from
base_image_url: https://mirror.bahnhof.net/pub/fedora/linux/releases/40/Cloud/x86_64/images/{{ base_image_name }}

# SHA256 for image
base_image_sha: ac58f3c35b73272d5986fa6d3bc44fd246b45df4c334e99a07b3bbd00684adee

# Where libvirt puts images by default
libvirt_pool_dir: "/var/lib/libvirt/images"

# Used in vm-template.xml file to reference new vm image
vm_image_name: "{{ libvirt_pool_dir }}/{{ vm_name }}.qcow2"

# Name of VM
vm_name: f40-test

# vCPUs for VM
vm_vcpus: 2

# Memory for VM
vm_ram_mb: 2048

# Name of libvirt network bridge we have created
vm_net: kvmtest

# Domain to use
libvirt_domain: kvmtest.net

# Root password, put in a vault
vm_root_pass: redhat123

# Location of SSH key
ssh_key: /home/mglantz/.ssh/id_rsa.pub

# Name of libvirt network
libvirt_net_name: "kvmtest"

# Libvirt bridge name (in Linux)
libvirt_bridge_name: virbr1
```

Dependencies
------------

https://docs.ansible.com/ansible/latest/collections/community/libvirt/index.html

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
- name: Deploys VM based on cloud image
  hosts: localhost
  gather_facts: yes
  become: yes
  vars:
    pool_dir: "/var/lib/libvirt/images"
    vm: f40-test02
    vcpus: 2
    ram_mb: 2048
    cleanup: no
    net: kvmtest
    ssh_pub_key: "/home/mglantz/.ssh/id_rsa.pub"

  tasks:
    - name: KVM Provision role
      include_role:
        name: libvirt-provision
      vars:
        libvirt_pool_dir: "{{ pool_dir }}"
        vm_name: "{{ vm }}"
        vm_vcpus: "{{ vcpus }}"
        vm_ram_mb: "{{ ram_mb }}"
        vm_net: "{{ net }}"
        cleanup_tmp: "{{ cleanup }}"
        ssh_key: "{{ ssh_pub_key }}"
```

License
-------

Apache License 2.0

Author Information
------------------

Magnus Glantz, sudo@redhat.com, 2024
