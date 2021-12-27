---
description: >-
  A short walkthrough of how to use manual SMTP open relay manually and also
  through an nmap script.
---

# SMTP Open Relay

### SMTP Open Relay Commands

```text
ncat -C <ip address>
HELO mail.co.uk
MAIL FROM: <user@mail.co.uk>
RCPT TO: <test@email.com>
DATA
Test Email
```

### Nmap Script

```text
nmap --script smtp-open-relay.nse [--script-args smtp-open-relay.domain=<domain>,smtp-open-relay.ip=<address>,...] -p 25,465,587 <host>
Host script results:
| smtp-open-relay: Server is an open relay (1/16 tests)
|_MAIL FROM:<antispam@insecure.org> -> RCPT TO:<relaytest@insecure.org>
```

