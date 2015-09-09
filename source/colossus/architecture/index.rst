:title: Colossus Architecture

Colossus Architecture
=====================

The Colossus is comprised of the following components:

* CoreOS - The Operating System
	* Etcd - The Distributed key-value store
	* Fleet - The Distributed init System
* Consul - The Service Discovery
	* Registrator - The Docker Bridge
	* HAProxy - The Proxy & Load Balancer
* Docker - The Container Runtime

Overview
--------

A ``wildcard DNS`` is configured to point all subdomains of the cluster network to a Virtual IP. The Virtual IP is configured to float inside the cluster.

A distributed service manages which node responds to the Virtual IP. If that node goes down, fleet migrates the VIP to another machine.

All nodes run an active-passive HAProxy that is auto-configured using Consul as Services Backend.

Consul runs as a cluster service that keeps track of the services running in the cluster and as DNS server internally to resolve services using DNS.

Registrator registers/deregisters automatically the Docker container instances to the Consul Backend.

Etcd is used to bootstrap Consul cluster.

**Usage Example**

Run an nginx server:

.. sourcecode:: bash

    docker run -d -p 80 -e SERVICE_NAME=example nginx

Open http://example.cluster.local to see the nginx server.

.. image:: /_static/images/deployment_environment.png
    :class: img-responsive img-thumbnail

CoreOS
------

`CoreOS <https://coreos.com/>`_ provides the Operating System layer. It comes with `Etcd <https://github.com/coreos/etcd>`_ service, a distributed highly-available key-value storage, and `Fleet <https://github.com/coreos/fleet>`_ a Distributed init System.

Docker
------

`Docker <https://www.docker.com/>`_ provides the abstraction of packaging and running apps as lightweight linux-based containers.

Consul
------

We use `Consul <https://www.consul.io/>`_ as a Service Discovery process.

Consul makes it simple for services to register themselves and to discover other services via a DNS or HTTP interface. Register external services such as SaaS providers as well.

Pairing service discovery with health checking prevents routing requests to unhealthy hosts and enables services to easily provide circuit breakers.

Registrator
-----------

`Registrator <http://gliderlabs.com/registrator/latest/>`_ automatically registers and deregisters services for any Docker container by inspecting containers as they come online.

HAProxy
-------

We use `HAProxy <http://www.haproxy.org/>`_ as reverse proxy and load balancing between instances of a service. The port 80 is listened by the HAProxy that monitors Consul service for existing services and re-configures itself to route traffic to the services using subdomains. For example for service ``stable`` the URL http://stable.coreos1.acme.local can be used if acme.local is the domain of the cluster and coreos1 is the name of a cluster node.


Colossus Features
-----------------

Colossus adds:

* Easy On-premise or on-Cloud deployment of platform
* Support for Firewall Proxy configuration
* Integration with existing Continuous Integration and Code Repository services
* Complete Workflow definition from commit push to automatic or on-demand deployment (Compile, package, test, push, deploy)
* Parity between git branches / tags and docker image versions for traceability
