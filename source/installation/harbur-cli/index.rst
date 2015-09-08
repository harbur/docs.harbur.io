:title: Install Harbur CLI

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
