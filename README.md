Ansible-Role-Kea
=========

A ansible role for installing and configuring isc-kea on Debian.

__Note! - This is Work In Progress__

Requirements
------------

- Debian
- Only tested with version 2.5 of Kea
- Only tested with ansible [core 2.16.3]
- Only tested with python 3.11


Role Variables
--------------
Most of the variables are listed below. For a complete list see `defaults/main.yml`. For details on a lot of them I would check the [Kea Administrator Reference Manual (ARM)](https://kea.readthedocs.io/en/latest/index.html)

    kea_version: 2.5

Default version of Kea that will be installed. This role with pull packages from the [Cloudsmith repository](https://cloudsmith.io/~isc/repos/) so please check there for available versions. 


    kea_interfaces: [ ]

A list of interfaces that kea-dhcp4 should listen to. You would likely put something like `[ 'eth0' ]` or `['*']` here.

    kea_subnets4: [ ]

A list of subnet configs that will be written as JSON to the dhcp4 config.


    kea_options4: [ ]


DHCP v4 Options like `domain-name-servers` and so on. For details look at  [Kea standard options](https://kea.readthedocs.io/en/kea-2.5.0/arm/dhcp4-srv.html#standard-dhcpv4-options)


    kea_dhcp4_ddns: no

Set to yes to enable ddns for dhcp4.


Dependencies
------------

- community.general


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
---
- hosts: servers
  vars:
    kea_interfaces: ['eth1']
    kea_subnets4:
      - subnet: "192.168.170.0/24"
        pools:
          - pool: "192.168.170.100 - 192.168.170.150"
  roles:
      - { role: kmpm.kea,}

```

License
-------

TBD

Author Information
------------------

https://github.com/kmpm
