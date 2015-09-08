:title: Install Docker

Install Docker
==============

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
