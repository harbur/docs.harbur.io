:title: Bootstrapping

Bootstrapping
=============

In order to bootstrap the Cluster the following steps should be made:

* `CoreOS - Installing to Disk <https://coreos.com/os/docs/latest/installing-to-disk.html>`_
* `CoreOS - Booting on DigitalOcean <https://coreos.com/os/docs/latest/booting-on-digitalocean.html>`_

**Stable** CoreOS distribution channel should be configured on all machines

**Etcd2** is used to connect the cluster nodes

**Consul** is used as Service Discovery

**Registrator** is used to monitor docker engine and publish new services to consul

**HAProxy** is used to redirect traffic to services. It actively monitors Consul to reconfigure traffic routing with changes on services
