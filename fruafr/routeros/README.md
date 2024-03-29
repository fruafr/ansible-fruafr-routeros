# ansible-fruafr-routeros

Ansible collection for Mikrotik RouterOs : print configuration, import or export files/backups

## Purpose

The purpose of this collection is to provide Ansible roles to perform high-level tasks on Routerboard such as printing configuration, import and export of files/backups.

It is NOT officially supported by Mikrotik.

## Introduction
[Mikrotik](https://mikrotik.com/aboutus) is a Latvian company developing routers, switches and ISP systems.

[RouterOS](https://mikrotik.com/software) is the operating system of RouterBoard products. It is [based on Linux kernel](https://help.mikrotik.com/docs/display/ROS/Getting+started). It powers MikroTik hardware devices, but is also available for virtual machines.

[RouterOS Documentation](https://help.mikrotik.com/docs/) is available.

## Playbooks
- get_facts.yml : Gather and print the system facts
- export_backup_encrypted.yml : Export the configuration to an encrypted file 
- export_script.yml :  Export the configuration as a plain text script
- file_get.yml: Download a file from the Mikrotik device
- file_put.yml: Copy a file to the Mikrotik device
- interface_bridge_print.yml: Print bridge interface details
- interface_ethernet_print.yml: Print ethernet interface details
- interface_print.yml : Print interface details
- interface_wireguard_print.yml: Print wireguard interface details
- interface_wireless_print.yml: Print wireless interface details
- ip_address_print.yml : Print the list of IPv4 addresses
- ip_route_print.yml : Print the IPv4 routes 
- system_clock_print.yml : Print the system [clock](https://help.mikrotik.com/docs/display/ROS/Clock)
- system_identity_print.yml : Print the system's [identity](https://help.mikrotik.com/docs/display/ROS/Identity)
- system_resource_print.yml : Gather and print the current system [resources](https://help.mikrotik.com/docs/display/ROS/Resource)
- system_routerboard_print.yml : Gather and print the [routerboard information](https://help.mikrotik.com/docs/display/ROS/RouterBOARD) (board, firmware version etc)
- user_print.yml: Print the list of users

## Roles
- fruafr.routeros.default_command: Execute a command with general command, subcommand and parameters
- fruafr.routeros.export_backup_encrypted: Export the configuration as an encrypted backup
- fruafr.routeros.export_script: Export the configuration as a plain text script
- fruafr.routeros.file_get: Download a file from the Mikrotik device
- fruafr.routeros.file_put: Copy a file to the Mikrotik device
- fruafr.routeros.get_facts : Gather and print the system facts
- fruafr.routeros.interface_print : Print interface details
- fruafr.routeros.ip_address_print : Print the list of IPv4 addresses
- fruafr.routeros.ip_route_print : Print the IPv4 routes 
- fruafr.routeros.system_clock_print : Print the system [clock](https://help.mikrotik.com/docs/display/ROS/Clock)
- fruafr.routeros.system_identity_print : Print the system's [identity](https://help.mikrotik.com/docs/display/ROS/Identity)
- fruafr.routeros.system_identity_set : Change the system's [identity](https://help.mikrotik.com/docs/display/ROS/Identity)
- fruafr.routeros.system_resource_print : Gather and print the current system [resources](https://help.mikrotik.com/docs/display/ROS/Resource)
- fruafr.routeros.system_routerboard_print : Gather and print the [routerboard information](https://help.mikrotik.com/docs/display/ROS/RouterBOARD) (board, firmware version etc)
- fruafr.routeros.user_print : Print the list of users

## Install the collection
`ansible-galaxy install fruafr.routeros`

## Pre-requirements on the machine running Ansible
- Under Debian or Ubuntu 
`sudo apt-get install sshpass`

- Install pylibssh
`pip3 install ansible-pylibssh`

## Known issues

### Corrupted files with Mikrotik

With ansible net common and libssh, files uploaded or downloaded from Mikrotik devices are corrupted.

[Issue](https://forum.mikrotik.com/viewtopic.php?t=190816) or [Ansible net common corrupted files](https://www.reddit.com/r/ansible/comments/w8p5pq/ansiblenetcommonnet_get_corrupted_files/) 

Solution : 

You MUST set in ansible.cfg:

[paramiko_connection]
look_for_keys = False

and the following variables in your inventory variables:

ansible_connection: ansible.netcommon.network_cli
ansible_network_os: community.routeros.routeros
ansible_network_cli_ssh_type: paramiko

### Answers to prompt

Does not support answers to prompt questions due to limitation in [community.routeros/issues/42](https://github.com/ansible-collections/community.routeros/issues/42)

## Technical details
This collection uses:
- The MikroTik CLI
- [community.network](https://docs.ansible.com/ansible/latest/collections/community/network/index.html): `ansible-galaxy collection install community.network`
    - [community.network.routeros_command](https://docs.ansible.com/ansible/latest/collections/community/routeros/command_module.html#ansible-collections-community-routeros-command-module)
- [community.routeros](https://docs.ansible.com/ansible/latest/collections/community/routeros/index.html): `ansible-galaxy collection install community.routeros`
- [ansible.netcommon](https://docs.ansible.com/ansible/latest/collections/ansible/netcommon/index.html): `ansible-galaxy collection install ansible.netcommon`

## Help needed
- Implementing answer to prompt questions in community.routeros and community.network.routeros_command
- Implementing long running processes (script execution on Mikrotik device)

## License
Licensed under the MIT License.

## Author
David Heurtevent <david@heurtevent.org>

## Copyright notice
Mikrotik and RouterOS are trademarks of SIA Mikrotīkls.