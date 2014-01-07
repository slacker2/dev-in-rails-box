# A Virtual Machine for Ruby on Rails Web Development

## Introduction

This repo is branched from the Rails Core development box (https://github.com/rails/rails-dev-box). This project automates the setup of a development environment for working with Ruby on Rails. Use this virtual machine to create websites and such.

## Requirements

* [VirtualBox](https://www.virtualbox.org)

* [Vagrant 1.1+](http://vagrantup.com) (not a Ruby gem)

## How To Build The Virtual Machine

Building the virtual machine is this easy:

    host $ git clone https://github.com/slacker2/dev-in-rails-box.git
    host $ cd dev-in-rails-box
    host $ vagrant up

That's it.

If the base box is not present that command fetches it first. The setup itself takes about 3 minutes in a MacBook Air. After the installation has finished, you can access the virtual machine with

    host $ vagrant ssh
    Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic-pae i686)
    ...
    vagrant@dev-in-rails-box:~$

Port 3000 in the host computer is forwarded to port 3000 in the virtual machine. Thus, applications running in the virtual machine can be accessed via localhost:3000 in the host computer.

## What's In The Box

* Git

* RVM

* Ruby 2.1.0 (binary RVM install)

* Bundler

* Rails

* SQLite3, MySQL, and Postgres

* System dependencies for nokogiri, sqlite3, mysql, mysql2, and pg

* Databases and users for a generic setup (you should probably change this?)

* Node.js for the asset pipeline


## Recommended Workflow

The recommended workflow is

* edit in the host computer and

* test within the virtual machine.

Just clone your Rails project into the dev-in-rails-box directory on the host computer:

    host $ ls
    README.md   Vagrantfile puppet
    host $ git clone git@github.com:<your username>/<your project>.git

Vagrant mounts that directory as _/vagrant_ within the virtual machine:

    vagrant@dev-in-rails-box:~$ ls /vagrant
    puppet  <your project>  README.md  Vagrantfile

Install gem dependencies in there:

    vagrant@dev-in-rails-box:~$ cd /vagrant/rails
    vagrant@dev-in-rails-box:/vagrant/rails$ bundle

We are ready to go to edit in the host, and test in the virtual machine.

This workflow is convenient because in the host computer you normally have your editor of choice fine-tuned, Git configured, and SSH keys in place.

## Virtual Machine Management

When done just log out with `^D` and suspend the virtual machine

    host $ vagrant suspend

then, resume to hack again

    host $ vagrant resume

Run

    host $ vagrant halt

to shutdown the virtual machine, and

    host $ vagrant up

to boot it again.

You can find out the state of a virtual machine anytime by invoking

    host $ vagrant status

Finally, to completely wipe the virtual machine from the disk **destroying all its contents**:

    host $ vagrant destroy # DANGER: all is gone

Please check the [Vagrant documentation](http://docs.vagrantup.com/v2/) for more information on Vagrant.

## License

Released under the MIT License, Copyright (c) 2012–<i>ω</i> Xavier Noria.
