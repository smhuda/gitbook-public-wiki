---
description: >-
  ipcalc takes an IP address and netmask and calculates the resulting broadcast,
  network, Cisco wildcard mask, and host range.
---

# IP Calculator

## Calculate IPs from a subnet:

```text
ipcalc 192.0.0.0/3
ipcalc 192.168.0.135
```

### Subnet Slicing:

Thanks to CIDR, we can finely slice and dice A, B, or C networks into multiple subnets, and ipcalc makes subnetting easy. Suppose you want to make two Class B subnets; just tell ipcalc the network segment you want to divide and how many hosts in each segment. In this example we want 15 hosts in each subnet:

```text
ipcalc 172.16.1.0/24 -s 15 15
```

