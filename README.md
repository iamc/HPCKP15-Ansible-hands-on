# HPCKP15-Ansible-hands-on

## Abstract
After the previous Ansible introductory talk we will walk through setting up a basic configuration for a
simple computing cluster created with virtual machines. As an introductory step we will briefly present
Vagrant, a tool which will allow us to create reproducible and portable virtual machine development and
testing environments.

Using a very simple Vagrant configuration file we will setup a test cluster with a head node and a few
computing nodes. Within the head node we will download Ansible, build a rpm package and install it. We
will then write the inventory file with nodes of different types, make some test runs and create a basic
Ansible playbook for eg. install some packages, distribute some configuration files and configure some
services both in the head and the computing nodes.

The Vagrant configuration file and virtual machine template (Vagrant "box") as well as the base Ansible
files we will use will be provided beforehand so that anyone interested will be able to follow along the
session in his/her laptop. Check https://github.com/iamc/HPCKP15-Ansible-hands-on for more
information.

## Prerequisites

We will use VirtualBox based virtual machines deployed with Vagrant, so in order to follow the tutorial you must have both [VirtualBox]() and [Vagrant]() installed in your laptopt.

 * VirtualBox: install it from your distribution repositories or straigth from [its webpage](https://www.virtualbox.org/wiki/Downloads)
 * Vagrant: just [download](https://www.vagrantup.com/downloads.html) the corresponding package and install it.

After installing them get the VirtualBox machine I prepared so that you have it ready for the hands-on session. It's a Scientific Linux 6.5 minimal install Vagrant "box" (virtual machine template) I created myself. Just add it to your Vagrant boxes (it's almost 600MB, so it may take a while)

    vagrant box add --name SL-65-x86_64-minimal https://dl.dropboxusercontent.com/u/49910137/scientific65_x86_64_minimal.box

or download it first and then add it

    wget https://dl.dropboxusercontent.com/u/49910137/scientific65_x86_64_minimal.box
    vagrant box add --name SL-65-x86_64-minimal scientific65_x86_64_minimal.box

Now we are ready to start playing. The Vagrant and Ansible configuration files will be provided later on.


