:title: Authenticating

Authenticating
--------------

In order to be able to access private repositories through the CLI environment you need to authenticate yourself. The following environment variables can be used for authentication:

* *HARBUR_USER*: The user login
* *HARBUR_PASSWD*: The user password

To configure your shell to avoid setting the variables each time you can append the following to your `.bashrc` (or your respective shell):

.. sourcecode:: bash

	export HARBUR_USER=myuser
	export HARBUR_PASSWD=mypass