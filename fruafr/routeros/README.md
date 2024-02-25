# ansible-fruafr-routeros

Ansible collection for Mikrotik RouterOs

## Purpose

The purpose of this collection is to provide Ansible roles to perform high-level tasks on Routerboard such as configuration, import and export of backups.

It is NOT officially supported by Mikrotik. Use it at your own risk.

Does not support answers to prompt questions due to limitation in [community.routeros/issues/42](https://github.com/ansible-collections/community.routeros/issues/42)

## Introduction
[Mikrotik](https://mikrotik.com/aboutus) is a Latvian company developing routers, switches and ISP systems.

[RouterOS](https://mikrotik.com/software) is the operating system of RouterBoard products. It is [based on Linux kernel](https://help.mikrotik.com/docs/display/ROS/Getting+started). It powers MikroTik hardware devices, but is also available for virtual machines.

[RouterOS Documentation](https://help.mikrotik.com/docs/) is available.

## Playbooks
- get_facts.yml : Gather and print the system facts
- system_identity_print.yml : Display the system's [identity](https://help.mikrotik.com/docs/display/ROS/Identity)
- system_resource_print.yml : Gather and display the current system [resources](https://help.mikrotik.com/docs/display/ROS/Resource)
- system_routerboard_print.yml : Gather and print the [routerboard information](https://help.mikrotik.com/docs/display/ROS/RouterBOARD) (board, firmware version etc)

## Roles
- fruafr.routeros.get_facts : Gather and print the system facts
- fruafr.routeros.system_identity_print : Display the system's [identity](https://help.mikrotik.com/docs/display/ROS/Identity)
- fruafr.routeros.system_identity_set : Change the system's [identity](https://help.mikrotik.com/docs/display/ROS/Identity)
- fruafr.routeros.system_resource_print : Gather and display the current system [resources](https://help.mikrotik.com/docs/display/ROS/Resource)
- fruafr.routeros.system_routerboard_print : Gather and print the [routerboard information](https://help.mikrotik.com/docs/display/ROS/RouterBOARD) (board, firmware version etc)


## Technical details
This collection uses:
- The MikroTik CLI
- [community.network](https://docs.ansible.com/ansible/latest/collections/community/network/index.html): `ansible-galaxy collection install community.network`
    - [community.network.routeros_command](https://docs.ansible.com/ansible/latest/collections/community/routeros/command_module.html#ansible-collections-community-routeros-command-module)
- [community.routeros](https://docs.ansible.com/ansible/latest/collections/community/routeros/index.html): `ansible-galaxy collection install community.routeros`
- [ansible.netcommon](https://docs.ansible.com/ansible/latest/collections/ansible/netcommon/index.html): `ansible-galaxy collection install ansible.netcommon`

## Install the collection
`ansible-galaxy install fruafr.routeros`

## Pre-requirements on the machine running Ansible
- Under Debian or Ubuntu 
`sudo apt-get install sshpass`

- Install pylibssh
`pip3 install ansible-pylibssh`

## Help needed
- Documentation of roles
- Tests
- Implementing answer to prompt questions in community.routeros and community.network.routeros_command

## License
Licensed under the MIT License.

## Author
David Heurtevent <david@heurtevent.org>

## Copyright notice
Mikrotik and RouterOS are trademarks of SIA Mikrotīkls.