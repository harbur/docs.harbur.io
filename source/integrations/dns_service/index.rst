:title: DNS Service

DNS Service
===========


DNS service should be configured so that the cluster nodes have their own name under the domain.

A fixed IP should be reserved for the Cluster as Virtual IP with it's own DNS name.

A wildcard DNS entry should also be configured in order to point to the Virtual IP.

In order to activate SSL connectivity, valid SSL certificates are needed for the DNS VIP and for each of the cluster nodes.
 
As an example, if the domain is acme.local and there are 3 CLM nodes the following are the proposed DNS entries with their respective SSL certificates:

* ``clm.acme.local``: Points to the Virtual IP
* ``*.clm.acme.local``: Points to the Virtual IP
* ``clm1.acme.local``: Points to the CLM node 1
* ``clm2.acme.local``: Points to the CLM node 2
* ``clm3.acme.local``: Points to the CLM node 3
* ``...``
