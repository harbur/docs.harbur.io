:title: Install Docker Compose

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
