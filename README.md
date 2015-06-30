#DNS Bootstrap

##Overview

Installs a basic DNS setup on a machine to bootstrap a network

##Description

This script is intended to be used on cloud images to provsion a domain name
service without the use of centralised configuration management.  Typically
this is deployed first to establish a domain authority to be used by
subsequent configuration management.

It first alters the network configuration be static and specify the requested
domain in /etc/resolv.conf, installs the required components and provisions
the nameserver with zones for the domain and a reverse zone for the subnet,
finally updating the network configuration again to point at the name server.
An SOA and NS record is created for the server.

Additional records can be added with nsupdate without specifying the RNDC key
the intent being the nameserver is used within a private cloud and new VM
instances can register themselves when created.

##Usage

```bash
./bootstrap example.com
```
