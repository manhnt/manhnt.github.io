---
layout: post
title: Netplan - Configure static IP address
categories: others
---

*Apply to Ubuntu Server 18.04.*

With netplan, to configure network interfaces, we have to edit the `*.yaml` files in `/etc/netplan/` directory.

Below is an example config to set a static IP address for enp0s3 ethernet interface:

```
network:
    ethernets:
        enp0s3:
            addresses:
              - 10.72.119.11/24
            gateway4: 10.72.119.254
            nameservers:
              addresses: [8.8.8.8, 1.1.1.1]
    version: 2
```

After saving the change, run `netplan apply` command to apply the change. This command must run with root permission.

