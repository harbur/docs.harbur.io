:title: Deployment Environment

Deployment Environment
======================

The deployment environment can be seen below:

.. image:: /_static/images/deployment_environment.png
    :class: img-responsive img-thumbnail

Each CoreOS node has it's own hostname and a ``wildcard DNS`` configuration to traffic all subdomains under the same machine.

We use `Consul <https://www.consul.io/>`_ as a Service Discovery process.

.. note::

   Consul makes it simple for services to register themselves and to discover other services via a DNS or HTTP interface. Register external services such as SaaS providers as well.

   Pairing service discovery with health checking prevents routing requests to unhealthy hosts and enables services to easily provide circuit breakers.

We use `Registrator <http://gliderlabs.com/registrator/latest/>`_ as a Service registry bridge for Docker.

.. note::
    Another use case for this is when you have a module with a C extension.


.. note::

	Registrator automatically registers and deregisters services for any Docker container by inspecting containers as they come online.

We use `HAProxy <http://www.haproxy.org/>`_ as reverse proxy and load balancing between instances of a service. The port 80 is listened by the HAProxy that monitors Consul service for existing services and re-configures itself to route traffic to the services using subdomains. For example for service ``stable`` the URL http://stable.coreos1.acme.local can be used if acme.local is the domain of the cluster and coreos1 is the name of a cluster node.

.. note::

	All parts are modular and can be removed/replaced by other implementations.
