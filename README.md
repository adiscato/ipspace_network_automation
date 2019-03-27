# ipspace_network_automation

## LAB SETUP ###
Brief description of network automation lab setup. 

---------------------------------------------------
## SUMMARY ##

The lab is created on the EVE - The Emulated Virtual Environment (https://www.eve-ng.net) which is installed on VMWare ESXi virtual host.
Goal is to be able to execute Ansible playbooks on the Cisco emulated devices in order to apply configuration templates.

On the same ESXi host two virtual machines are installed:

•	EVE NG

•	Ubuntu Linux

--------------------------------------------------
## NETWORK SETUP ##

For the connection between virtual machines, vswitch is configured, Ubuntu VM is also connected to the internet to be able to download necessary file packages such as Ansible, etc.

On the EVE NG lab topology is created and it contains:

•	Network to the Ubuntu Linux VM ens192 network adapter

•	Emulated Cisco IOS routers and switches

-----------------------------------------------------
## UBUNTU VM DETAILS ##

Information about Ubuntu Linux VM:

Ubuntu distribution details:

adisc@ubuntu-ipspace:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:        18.04
Codename:       bionic

Network details:

To internet:

ens160: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.12.113.37  netmask 255.255.255.0  broadcast 10.12.113.255
        inet6 fe80::20c:29ff:fe5d:2789  prefixlen 64  scopeid 0x20<link>

To EVE NG:

ens192: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.10.2  netmask 255.255.255.0  broadcast 192.168.10.255
        
-------------------------------------------------------------------------
## ANSIBLE DETAILS ##

Ansible version:

adisc@ubuntu-ipspace:~$ ansible --version
ansible 2.7.9
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/adisc/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.15rc1 (default, Nov 12 2018, 14:31:15) [GCC 7.3.0]

----------------------------------------------------------------------------

## SETUP VERIFICATION ##

Verification requested in the task description:

- SSH from your Ansible host to all network devices using usernames/passwords or SSH keys

adisc@ubuntu-ipspace:/etc/ansible$ ssh adisc@192.168.10.4
Password:
access-switch-02#

- Execute commands on your network devices with Ansible raw module.

adisc@ubuntu-ipspace:/etc/ansible$ ansible all -i ./hosts -m raw -a "show run |i hostname" -u adisc -k
SSH password:


192.168.10.4 | CHANGED | rc=0 >>
hostname access-switch-02
Shared connection to 192.168.10.4 closed.

-----------------------------------------------------------------------------------




