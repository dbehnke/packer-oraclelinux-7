# packer-oraclelinux-7

Builds an Oracle Linux 7 Installation for VirtualBox and Vmware (Untested) using packer and vagrant.

Template is based off of https://github.com/opscode/bento/blob/master/packer/centos-7.0-x86_64.json

## Prerequisites

1. Packer - http://packer.io

2. Vagrant - http://vagrantup.com

3. VirtualBox - http://virtualbox.org  (VMWare may work but was not tested)

4. Oracle Linux 7 ISO - https://edelivery.oracle.com/linux

5. Download the OracleLinux-R7-U0-Server-x86_64-dvd.iso image.*

## Build Instructions

1. Clone the repository

        $ git clone https://github.com/dbehnke/packer-oraclelinux-7.git
        $ cd packer-oraclelinux-7

2. Install the prerequisites, make sure the packer and vagrant commands are in your PATH and callable from Terminal/Command Prompt

3. Place OracleLinux-R7-U0-Server-x86_64-dvd.iso in the iso folder

4. Build the image

        $ packer build -only=virtualbox-iso ol-7.0-x86_64.json

5. Add to vagrant

        $ vagrant box add ol7 oraclelinux-7.0_chef-provisionerless.box

6. Test with vagrant

```
$ mkdir ol7-test
$ cd ol7-test
$ vagrant init ol7
$ vagrant up
$ vagrant ssh
```

Sample:

```
$ mkdir ol7-test

$ cd ol7-test

$ vagrant init ol7
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.

$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'ol7'...
==> default: Matching MAC address for NAT networking...
==> default: Setting the name of the VM: ol7-test_default_1406232534352_11563
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 => 2222 (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection timeout. Retrying...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
==> default: Mounting shared folders...
    default: /vagrant => /Users/dbehnke/Development/packer-ol7/ol7-test

$ vagrant ssh
Last login: Thu Jul 24 19:48:41 2014 from 10.0.2.2

[vagrant@localhost ~]$ cat /etc/redhat-release
Red Hat Enterprise Linux Server release 7.0 (Maipo)
```
