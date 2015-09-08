:title: Installation


Installation
============

This section describes the necessary tools for the developer to get started with containers and interact with the system.

* Install `Docker <https://www.docker.com/>`_
* Install `Docker Compose <https://docs.docker.com/compose/>`_
* Install `Harbur Captain <https://github.com/harbur/captain>`_
* Install `Harbur CLI <https://github.com/harbur/harbur-cli>`_
* Install `CoreOS Etcd CLI <https://github.com/coreos/etcdctl>`_
* Install `CoreOS Fleet CLI <https://github.com/coreos/fleet>`_

Install Docker
--------------

Docker is a CLI tool to create, manage and run containers.

To install Docker follow the instructions provided in `Docker website <https://docs.docker.com/installation>`_.

A quick-start guide is to launch the following script:

.. sourcecode:: bash

    curl -sSL https://get.docker.com/ | sh

To validate docker installation, run the following command:

.. sourcecode:: bash

    docker run --rm hello-world

This will check that you can download images from the public hub, and run a container properly.

If you have a private repository, then also check you can login and pull correctly from it.

Install Docker Compose
----------------------

Docker Compose is a CLI tool to define and run multi-container applications with Docker.

To install Docker Compose follow the instructions provided in `Docker website <https://docs.docker.com/compose/install/>`_.

A quick-start guide is to launch the following script:

.. sourcecode:: bash

    curl -L https://github.com/docker/compose/releases/download/1.4.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose

To validate installation, run the following command:

.. sourcecode:: bash

    docker-compose version

It should respond with the appropriate version number.

Install Harbur Captain
----------------------

Captain is a CLI build tool that converts Git workflow to Docker containers.

To install Captain follow the instructions provided in `Captain repo <https://github.com/harbur/captain>`_.

A quick-start guide is to launch the following script:

.. sourcecode:: bash

    curl -L https://github.com/harbur/captain/releases/download/v0.7.0/captain-`uname -s`-`uname -m` > /usr/local/bin/captain
    chmod +x /usr/local/bin/captain

To validate installation, run the following command:

.. sourcecode:: bash

    captain version

It should respond with the appropriate version number.

Install Harbur CLI
------------------

Harbur CLI is a tool to discover and use docker-compose and fleet recipes.

To install Harbur CLI follow the instructions provided in Harbur CLI repo.

A quick-start guide is to launch the following script:

In order to getting started with Harbur, the first step is to install the Harbur CLI:

.. sourcecode:: bash

    curl -L https://raw.githubusercontent.com/harbur/harbur-cli/master/harbur > /usr/local/bin/harbur
    chmod +x /usr/local/bin/harbur

To validate installation, run the following command:

.. sourcecode:: bash

    harbur harbur/wordpress up -d

It should download the docker-compose recipe for wordpress and launch it locally (wordpress + mysql).

To check the port where wordpress is running do:

.. sourcecode:: bash

    harbur harbur/wordpress port web 80

To stop the stack run:

.. sourcecode:: bash

     harbur harbur/wordpress kill
     harbur harbur/wordpress rm -v

**Help screen**

To check if installation is succesful you can try the following:

.. sourcecode:: bash

	harbur --help

	Harbur CLI tool - container stacks management with Docker Compose.

	Usage:
	  harbur IMAGE COMMAND

	Download a docker-compose.yml and launch docker-compose command on it.
	If docker-compose.yml is already downloaded it is cached at ~/.harbur/ directory
	IMAGE is defined by 'namespace/repo:version'

Install CoreOS Etcd CLI
-----------------------

Etcd is the distributed key-value storage on CoreOS.

The client for etcd (etcdctl), can be installed on remote machines and they can connect with the cluster.

In order to install it in Mac do:

.. sourcecode:: bash

    brew install etcd

Install CoreOS Fleet CLI
------------------------

Fleet is a Distributed init System on CoreOS.

The client for fleet (fleetctl), can be installed on remote machines and they can connect with the cluster.

In order to install it in Mac do:

.. sourcecode:: bash

    brew install fleetctl

To configure fleetctl, add the following content on the ~/.harburrc file

.. sourcecode:: bash

    export FLEETCTL_TUNNEL=node1.cluster.local

where **node1** is the cluster node used as Fleet tunnel and **cluster.local** is the domain used for your cluster.

Make sure to load the script on your .bashrc by appending the following line at the bottom:

.. sourcecode:: bash

    . ~/.harburrc

to load it on your running terminal do:

.. sourcecode:: bash

    source ~/.harburrc

NOTE: You need ssh access to that machine in order to be able to communicate with fleet.

To validate installation, run the following command:

.. sourcecode:: bash

    fleetctl list-units

It should return a list of the loaded units in fleet.