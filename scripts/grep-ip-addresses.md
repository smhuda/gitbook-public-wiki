---
description: A grep command to get all IP addresses contained in a text file
---

# Grep IP Addresses

A grep command to get all IP addresses contained in a text file:

```text
$ grep -Eo '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' IPs-To-Grep.txt > Grepped-ips.txt
```



