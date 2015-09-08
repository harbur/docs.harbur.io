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

Authenticating
--------------

In order to be able to access private repositories through the CLI environment you need to authenticate yourself. The following environment variables can be used for authentication:

* *HARBUR_USER*: The user login
* *HARBUR_PASSWD*: The user password

To configure your shell to avoid setting the variables each time you can append the following to your `.bashrc` (or your respective shell):

.. sourcecode:: bash

	export HARBUR_USER=myuser
	export HARBUR_PASSWD=mypass

Troubleshooting
---------------

**Insecure mode**

If you get the following error:

.. sourcecode:: bash

	$ harbur user/image up -d
	Creating project_image_1...
	Pulling image repo/user/image:1.0.0...
	Traceback (most recent call last):
	File "<string>", line 3, in <module>
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.main", line 31, in main
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.docopt_command", line 21, in sys_dispatch
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.command", line 27, in dispatch
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.docopt_command", line 24, in dispatch
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.command", line 59, in perform_command
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.main", line 464, in up
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.project", line 208, in up
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.service", line 214, in recreate_containers
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.service", line 197, in create_container
	File "/code/build/docker-compose/out00-PYZ.pyz/docker.client", line 710, in pull
	File "/code/build/docker-compose/out00-PYZ.pyz/docker.auth.auth", line 67, in resolve_repository_name
	File "/code/build/docker-compose/out00-PYZ.pyz/docker.auth.auth", line 46, in expand_registry_url
	docker.errors.DockerException: HTTPS endpoint unresponsive and insecure mode isn't enabled.


This is probably because you use a private repository with HTTPS, without valid certificates. In order to continue you need to explicitly allow insecure connection:

.. sourcecode:: bash

	harbur user/image up -d --allow-insecure

**Permission Denied**

.. sourcecode:: bash

	$ harbur user/image up -d
	Creating project_image_1...
	Pulling image repo/user/image:1.0.0...
	Traceback (most recent call last):
	File "<string>", line 3, in <module>
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.main", line 31, in main
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.docopt_command", line 21, in sys_dispatch
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.command", line 27, in dispatch
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.docopt_command", line 24, in dispatch
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.command", line 59, in perform_command
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.cli.main", line 464, in up
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.project", line 208, in up
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.service", line 214, in recreate_containers
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.service", line 199, in create_container
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.progress_stream", line 37, in stream_output
	File "/code/build/docker-compose/out00-PYZ.pyz/compose.progress_stream", line 50, in print_output_event
	compose.progress_stream.StreamOutputError: Error: Status 403 trying to pull repository repo/user/image:1.0.0: "{\"error\": \"Permission Denied\"}"

You need to authenticate to your private repository:

.. sourcecode:: bash

	docker login repo

(Where repo is your private repository URL)

To verify connectivity try pulling with docker directly:

.. sourcecode:: bash

	docker pull repo/user/image:1.0.0

If that works, then you might be using an old docker-compose version which doesn't support pulling from private repositories. Update your docker-compose (version 1.3.0+) and try again.
