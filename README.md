

## Prerequisites

We will use VirtualBox based virtual machines deployed with Vagrant, so in
order to follow the tutorial you must have both [VirtualBox]() and [Vagrant]()
installed in your laptop.

 * VirtualBox: install it from your distribution repositories or straigth from [its webpage](https://www.virtualbox.org/wiki/Downloads)
 * Vagrant: Installing vagrant is trivial, just a matter of donwloading the installer/package and installing it. See the [Vagrant install documentation](https://docs.vagrantup.com/v2/installation/index.html). 

After installing them get the VirtualBox machine template I prepared so that
you have everything ready for the hands-on session. It's a Scientific Linux 6.5
minimal install Vagrant "box" (virtual machine template) I created myself. Just
download it (almost 600MB) and add it to the Vagrant boxes

    wget https://dl.dropboxusercontent.com/u/49910137/scientific65_x86_64_minimal.box
    vagrant box add --name SL-65-x86_64-minimal scientific65_x86_64_minimal.box

If you want to follow the hands-on tutorial clone this repository and bootstrap Vagrant. As we are using Ansible itself for the initial cluster bootstrap this will take some time: it will setup epel repository, install some packages, etc., which takes some time, specially the first time you do it. 

    git clone https://github.com/iamc/HPCKP15-Ansible-hands-on.git
    vagrant up

If you are new to Vagrant, ``vagrant`` command will give you some usage guidelines.


## Abstract

The way to manage the configuration of computing nodes in HPC clusters is
normally through, first, the use of some kind of master image deployed to the
nodes and, second, a "post configuration" stage in which the installed system
is modified in order to adapt it to the changes made to this base image:
modified SLURM configuration files, new filesystems to be mounted, updated
packages, new monitoring tools to be installed, etc.

One way to deal with this post-configuration stage, and also with further
changes which happen along the life of a computing node, is using a
Configuration Management System - CMS. CMS's, such as CFEngine, Puppet, Chef,
Salt, etc., are specifically designed to deal with system configuration changes
and to mantain consistency in complex systems: they allow us to define nodes'
service states, configuration files,
packages installed, mount points, security policies and much more.

But this also comes with a price: a steep learning curve and the CMS system
setup itself. Here we will present Ansible, a very easy to use CMS which, with
its clientless (zero initial setup in the nodes) push model and the simple,
human readable syntax of its YAML configuration files, perfectly fits the
mindset of HPC cluster administrators.

We will walk through setting up a basic
configuration for a simple computing cluster created with virtual machines. As
an introductory step we will briefly present Vagrant, a tool which will allow
us to create reproducible and portable virtual machine development and
testing environments.

Using a very simple Vagrant configuration file we will setup a test cluster
with a head node and a few computing nodes. Within the head node we will
have Ansible installed, we will then write the inventory file with nodes of
different types, make some test runs and create a basic Ansible playbook for
eg. install some packages, distribute some configuration files and configure
some services both in the head and the computing nodes.

