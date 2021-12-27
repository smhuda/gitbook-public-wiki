---
description: Error relating to no matching host key for SSH connection
---

# SSH Key

### Error:

```text
SSH returns: no matching host key type found. Their offer: ssh-dss
```

### Solution:

```text
ssh -oHostKeyAlgorithms=+ssh-dss root@192.168.8.109
```

