---
layout: post
title:  "Infoblox Integration with Ansible"
date:   2018-10-15
excerpt: "Integrating Ansible with Infoblox to perform DNS updates"
tag:
- Ansible
comments: true
---

Ansible 2.5 now supports Infoblox modules. Here are the modules, which have now been added:

nios_host_record – configure host records
nios_network – configure networking objects
nios_network_view – configure networking views
nios_dns_view – configure DNS views
nios_zone – configure DNS zones
I decided to design and deploy this setup in our working environment to update DNS entries using Ansible. Here are the steps which may need to be followed to get a working setup.

I would recommend to have a CentOS 7 or above system as the base level OS for this setup.
Next, install Ansible using “yum install ansible” command and make sure that you have Ansible 2.5 installed on your control node.

If the 2.5 version doesn’t get installed (happened in my case) then manually install Ansible 2.5.
Next, make sure that pip and all the required python dev tools are installed. If not, install them using the “yum install python-devel” command.

Once all the required tools and pip have been installed, install the Infoblox client on the control node using the following command “pip install infoblox-client”.

Once you have Infoblox-client and Ansible 2.5 installed on the control node then you should have a working setup to play with the Infoblox modules for Ansible.

At this point, you should be ready to write your first playbook to update DNS entries using Ansible.

Here’s an example of a working playbook which I wrote to update DNS entries:
``` yml
---
- name: Updating Infoblox using Ansible
  hosts: localhost
  connection: local
  gather_facts: no

tasks:

– name: Add DNS entries
  nios_host_record:
    name: “{{ item.hostname }}”
    ipv4:
      – address: “{{ item.IP }}”
    state: present
    comment: Modify this (For e.g = Assigned to John Doe)
    provider:
    host: “IP address of  Infoblox system”
    username: “Username to log into the Infoblox system”
    password: “Password to log into the Infoblox system” 
  with_items:
    – { hostname: ‘fqdn’, IP: ‘1.2.3.4’ }
```
Create a playbook similar to this and save it with the .yml extension.
cd into the directory where the playbook is and run the command “ansible-playbook playbookname.yml”
Once this playbook runs, it would update a DNS entry and assign a FQDN to the IP mentioned in the playbook.
