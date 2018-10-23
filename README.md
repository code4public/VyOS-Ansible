# vyos-ansible
This code is slightly different from the previous version of Ansible Playbook for VyOS.

There are 4 playbooks, as given below:
vyos-set-eth-vm1.yml
vyos-set-eth-vm2.yml
vyos-set-eth-vm3.yml
vyos-set-eth-vm4.yml

Above playbooks work on the follwing Ansible inventory.

Modify "/etc/ansible/hosts" file to include following entries.

# Ex 1: Ungrouped hosts, specify before any group headers.
vyos-node1
vyos-node2
vyos-node3
vyos-node4

# Ex 2: A collection of hosts belonging to the 'webservers' group
[vyos]
vyos-test-node
vyos-node1
vyos-node2
vyos-node3
vyos-node4

Download and run VyOS VMs from https://vyos.io adding 2 more ethernet vNICs, to be configured via ansible.

Here is the straight download link as of this writing.
https://downloads.vyos.io/release/1.1.8/vyos-1.1.8-amd64.ova

Install and configure 4 such VMs, and edit your Ansible host with their IP addresses.

root@ansible-master:/opt/vyos# cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       debian
192.168.140.170 ansible-master
192.168.140.171 ansible-host1
192.168.140.172 ansible-host2
192.168.140.173         vyos-test-node
192.168.140.174         vyos-node1
192.168.140.175         vyos-node2
192.168.140.176         vyos-node3
192.168.140.177         vyos-node4

After finishing above steps, run the ansible playbooks to configure desired IP addres on the VyOS routers.

Host      LAN1    LAN2        LAN3
VyOS-VM-1 Default 10.1.2.101  172.16.2.101
VyOS-VM-2 Default 10.1.2.102  172.16.2.102
VyOS-VM-3 Default 10.1.2.103  172.16.2.103
VyOS-VM-4 Default 10.1.2.104  172.16.2.104

Our aim here is to automate configuring the VM IP addresses as per the table given above.
