:title: Colossus

Colossus
========

Welcome to the Colossus documentation. Here you'll find information and resources to help you learn about Harbur Colossus Project. From getting starting with creating your first app to using the advanced features, these resources explain how to setup and manage your Colossus Platform.

Colossus is layered architecture designed to compose a clustered Docker infrastructure ready to be used for development, testing or production environments. It focuses on easy maintenance, upgradability, and minimizing downtimes through redundancy and no SPOF (Single Point of Failures).

What are the Layers?
--------------------

* `CoreOS <https://coreos.com/>`_ provides the OS layer. It comes with `Etcd <https://github.com/coreos/etcd>`_ service, a distributed highly-available key-value storage, and `Fleet <https://github.com/coreos/fleet>`_ a Distributed init System.
* `Docker <https://www.docker.com/>`_ provides the abstraction of packaging and running apps as lightweight linux-based containers.

Colossus adds:

* Easy On-premise or on-Cloud deployment of platform
* Support for Firewall Proxy configuration
* Integration with existing Continuous Integration and Code Repository services
* Complete Workflow definition from commit push to automatic or on-demand deployment (Compile, package, test, push, deploy)
* Parity between git branches / tags and docker image versions for traceability
