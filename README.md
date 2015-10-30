# ansible-meteor

A simple provision script to create a Linux machine and run a Meteor project inside it.

The project has been inspired by [this one](https://github.com/westonplatter/example_meteor_deploy), but since it didn't work for me from the beginning, I decided to create another Vagrant machine and provision it with a new series of Ansible scripts.

## Prerequisites

- VirtualBox
- Vagrant
- Ansible

## Install

Just clone the repository, run `vagrant up` and wait. When the script has deployed the VM, ssh into it with `vagrant ssh`, go to /vagrant/app/ and execute `meteor`.

Good luck with your new Meteor project!