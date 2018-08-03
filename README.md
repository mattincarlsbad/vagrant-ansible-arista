# vagrant-ansible-arista

Get started!
https://www.vagrantup.com/docs/getting-started/

## Network
The Vagrantfile in this repo will build the below network using Arista vEOS VMs running in Virtualbox.  Try it, it's so easy!
```bash
  mgmt-net          mgmt-net
     |                 |
+----1-----+      +----1-----+
|  spine1  |      |  spine2  |
|          |      |          |
+--2------3+      +2------3--+    mgmt-net
   |      |        |      |          |
   |      |        |      |     +----1-----+
   |      +-----------+   |     | ansible  |
   |               |  |   |     |          |
   |   +-----------+  |   |     +----------+
   |   |              |   |
+--2---3---+      +---2---3--+   
|          4------4          |
|  leaf1   5------5   leaf2  |
+----1-----+      +-----1----+
     |                  |   
  mgmt-net           mgmt-net
```

## Installation
1. Install Virtualbox on Windows, Mac, Linux, etc.
   https://www.virtualbox.org/wiki/Downloads
2. Install Vagrant
   https://www.vagrantup.com/downloads.html
3. Install Git (optional) https://git-scm.com/downloads
3. Create a directory for running the vagrant-arista lab:
   ex: U:\vagrant\arista>
4. Copy the "Vagrantfile" contents from this repo to the new directory. 
   Using git: "git clone https://github.qualcomm.com/itnet-dc/vagrant-ansible-arista"
   Or just copy/paste.  Be sure to name the file "Vagrantfile".
5. Download the Arista vEOS image to the same directory, or post it on a web server in your network.

## Vagrantup!
1. Start the lab by using the "vagrant up" command in the vagrant-ansible-arista directory:
```bash
[mattt1-mac:~/vagrant/vagrant-ansible-arista] mattt% vagrant up
Bringing machine 'leaf1' up with 'virtualbox' provider...
Bringing machine 'leaf2' up with 'virtualbox' provider...
Bringing machine 'spine1' up with 'virtualbox' provider...
Bringing machine 'spine2' up with 'virtualbox' provider...
Bringing machine 'ansible' up with 'virtualbox' provider...
==> leaf1: Importing base box 'vEOS-lab-4.18.5M-virtualbox.box'...
==> leaf1: Matching MAC address for NAT networking...
<snip>
```
2. Check the status of the Arista switch VM's:
```bash
[mattt1-mac:~/vagrant/vagrant-ansible-arista] mattt% vagrant status
Current machine states:

leaf1                     running (virtualbox)
leaf2                     running (virtualbox)
spine1                    running (virtualbox)
spine2                    running (virtualbox)
ansible                   running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
[mattt1-mac:~/vagrant/vagrant-ansible-arista] mattt%
```

## SSH to Your Arista VMs 
Use the "FastCli" command to enter EOS
```bash
[mattt1-mac:~/vagrant/vagrant-ansible-arista] mattt% vagrant ssh leaf1

Arista Networks EOS shell

-bash-4.3# FastCli
leaf1>show version
Arista vEOS
Hardware version:    
Serial number:       
System MAC address:  0800.2732.f493

Software image version: 4.18.5M
Architecture:           i386
Internal build version: 4.18.5M-6710299.4185M
Internal build ID:      3d3db99a-d291-4527-86d2-b296f4998d48

Uptime:                 24 minutes
Total memory:           1893384 kB
Free memory:            885364 kB

leaf1>

```

## Run the Crawl/Walk Ansible Playbooks on the vEOS Switches
SSH to the Ansible VM, and run the Crawl/Walk playbooks from Github: https://github.com/mattincarlsbad/ansible-arista-training-vagrant
```bash
[mattt1-mac:~/vagrant/vagrant-ansible-arista] mattt% vagrant ssh ansible
Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.4.0-87-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
 
vagrant@ubuntu:~$ cd ansible-arista-training-vagrant/
vagrant@ubuntu:~/ansible-arista-training-vagrant$ ls
crawl  README.md  walk
vagrant@ubuntu:~/ansible-arista-training-vagrant$ 
```
Follow the steps on the https://github.com/mattincarlsbad/ansible-arista-training-vagrant readme page for running the crawl and walk playbooks.

Enjoy!

## Shutdown/destroy all VM's
When you want to kill all VM's, use the following command:

vagrant destroy -f
