:title: Install CoreOS Fleet CLI

Install CoreOS Fleet CLI
------------------------

Fleet is a Distributed init System on CoreOS.

The client for fleet (fleetctl), can be installed on remote machines and they can connect with the cluster.

In order to install it in Mac do:

.. sourcecode:: bash

    brew install fleetctl

In order to install it in Ubuntu do:

.. sourcecode:: bash

  git clone https://github.com/coreos/fleet.git
  cd fleet
  git checkout TAG_VERSION
  ./build-docker
  sudo mv bin/fleetctl /usr/local/bin/

Note: Check your cluster's fleetctl version to set the adequate TAG_VERSION.

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

