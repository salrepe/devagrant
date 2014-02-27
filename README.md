devagrant
=========

A vagrant box with a minimum setup 

## Requirements

* [VirtualBox](https://www.virtualbox.org)
* [Vagrant](http://vagrantup.com)

## Starting the machine

```zsh
$ git clone git@github.com:salrepe/devagrant.git
$ cd devagrant
$ vagrant plugin install vagrant-berkshelf
$ vagrant up
$ vagrant provision
$ vagrant ssh
```

## Cookboks

* postgresql
* ruby_build
* rbenv
* vim
* git
