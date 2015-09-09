:title: Colossus

Colossus
========

Welcome to the Harbur Colossus Platform documentation!

Here you'll find information and resources to help you learn about Harbur Colossus Platform. From getting starting with creating your first app to using the advanced features, these resources explain how to setup and manage your Colossus.

Colossus is layered architecture designed to compose a clustered Docker infrastructure ready to be used for development, testing or production environments. It focuses on easy maintenance, upgradability, and minimizing downtimes through redundancy and NO-SPOF (No Single Point of Failures), the base for creating a fault-tolerant, self-healing and scalable solution.

What are the Layers?
--------------------

The Colossus is based on `CoreOS <https://coreos.com/>`_ for the Operating System, `Docker <https://www.docker.com/>`_ for the Container Runtime, and `Consul <https://www.consul.io/>`_ for the Service Discovery.

* `CoreOS <https://coreos.com/>`_ provides the OS layer. It comes with `Etcd <https://github.com/coreos/etcd>`_ service, a distributed highly-available key-value storage, and `Fleet <https://github.com/coreos/fleet>`_ a Distributed init System.
* `Docker <https://www.docker.com/>`_ provides the abstraction of packaging and running apps as lightweight linux-based containers.
* `Consul <https://www.consul.io/>`_ makes it simple for services to register themselves and to discover other services via a DNS or HTTP interface. Register external services such as SaaS providers as well.

Colossus adds:

* Easy On-premise or on-Cloud deployment of platform
* Support for Firewall Proxy configuration
* Integration with existing Continuous Integration and Code Repository services
* Complete Workflow definition from commit push to automatic or on-demand deployment (Compile, package, test, push, deploy)
* Parity between git branches / tags and docker image versions for traceability
