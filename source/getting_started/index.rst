:title: Getting Started


Getting Started
===============


Installing Harbur CLI
---------------------

In order to getting started with Harbur, the first step is to install the Harbur CLI:

.. sourcecode:: bash

	curl -s https://raw.githubusercontent.com/harbur/harbur-cli/master/harbur > /usr/local/bin/harbur

Help screen
-----------

To check if installation is succesful you can try the following:

.. sourcecode:: bash

	harbur --help

	Harbur CLI tool - container stacks management with Docker Compose.

	Usage:
	  harbur IMAGE COMMAND

	Download a docker-compose.yml and launch docker-compose command on it.
	If docker-compose.yml is already downloaded it is cached at ~/.harbur/ directory
	IMAGE is defined by 'namespace/repo:version'

