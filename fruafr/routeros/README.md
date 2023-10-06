# ansible-fruafr-routeros

Ansible collection for Mikrotik RouterOs

## Purpose

The purpose of this collection is to provide Ansible roles to perform high-level tasks on Routerboard such as configuration, import and export of backups.

It is NOT officially supported by Mikrotik. Use it at your own risk.

## Introduction
[Mikrotik](https://mikrotik.com/aboutus) is a Latvian company developing routers, switches and ISP systems.

[RouterOS](https://mikrotik.com/software) is the operating system of RouterBoard products. It is [based on Linux kernel](https://help.mikrotik.com/docs/display/ROS/Getting+started). It powers MikroTik hardware devices, but is also available for virtual machines.

[RouterOS Documentation](https://help.mikrotik.com/docs/) is available.

## Technical details
This collection uses:
- The MikroTik CLI
- [community.routeros](https://docs.ansible.com/ansible/latest/collections/community/routeros/index.html): `ansible-galaxy collection install community.routeros`
- [ansible.netcommon](https://docs.ansible.com/ansible/latest/collections/ansible/netcommon/index.html): `ansible-galaxy collection install ansible.netcommon`

## Install the collection
`ansible-galaxy install fruafr.routeros`

## Pre-requirements on the machine running Ansible
- Under Debian or Ubuntu 
`sudo apt-get install sshpass`

- Install pylibssh
`pip3 install ansible-pylibssh`

## License
Licensed under the Apache License, Version 2.0.

## Author
David Heurtevent <david@heurtevent.org>

## Copyright notice
Mikrotik and RouterOS are trademarks of SIA Mikrotīkls.