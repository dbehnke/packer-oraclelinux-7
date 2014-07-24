# Oracle Linux 7 - Build with Packer, Use with Vagrant

Builds an Oracle Linux 7 Installation for VirtualBox and Vmware (Untested) using packer and vagrant.

Template is based off of https://github.com/opscode/bento/blob/master/packer/centos-7.0-x86_64.json 

## Prerequisites

1.  Packer - http://packer.io

2.  Vagrant - http://vagrantup.com

3.  VirtualBox - http://virtualbox.org  (VMWare may work but was not tested)

4.  Oracle Linux 7 ISO - https://edelivery.oracle.com/linux

Download the OracleLinux-R7-U0-Server-x86_64-dvd.iso image.

## Build Instructions

1.  Clone the repository

    $ git clone https://github.com/dbehnke/packer-oraclelinux-7.git 
    
    $ cd packer-oraclelinux-7

2.  Install the prerequisites, make sure the packer and vagrant commands are in your PATH and callable from Terminal/Command Prompt

3.  Place OracleLinux-R7-U0-Server-x86_64-dvd.iso in the iso folder

4.  Build the image

    $ packer build -only=virtualbox-iso ol-7.0-x86_64.json

5.  Import into vagrant

    TODO

6.  Test with vagrant

    TODO