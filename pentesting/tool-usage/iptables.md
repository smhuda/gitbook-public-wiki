---
description: 'A mini wiki to refer to adding, delete or amending Iptables rules'
---

# Iptables

### List Specific Chain:

```text
sudo iptables -S TCP
```

### List Rules as Tables

```text
sudo iptables -L
sudo iptables -L INPUT
```

### Show Packet Counts and Aggregate Size

```text
sudo iptables -L INPUT -v
```

### Delete Rule by Specification

```text
sudo iptables -D INPUT -m conntrack --ctstate INVALID -j DROP
```

```text
sudo iptables -L --line-numbers
```

### Flush Chains

```text
sudo iptables -F INPUT
sudo iptables -F

```

### References:

* [https://www.digitalocean.com/community/tutorials/how-to-list-and-delete-iptables-firewall-rules](https://www.digitalocean.com/community/tutorials/how-to-list-and-delete-iptables-firewall-rules)

