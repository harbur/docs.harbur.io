:title: Install Harbur Captain

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
