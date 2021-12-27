---
description: >-
  Secure copy protocol is a means of securely transferring computer files
  between a local host and a remote host or between two remote hosts. It is
  based on the Secure Shell protocol. "SCP" commonly ref
---

# Secure Copy Protocol \(SCP\)

## Transferring from remote to host:

```text
sudo scp user@192.168.1.2:/home/john/evidence-output* /home
```

### Copy the remote file to the localhost:

```text
scp your_username@192.168.0.10:<remote_file> /some/local/directory
```

### Copy the local file to the remote host:

```text
scp <local_file> your_username@192.168.0.10:/some/remote/directory
```

