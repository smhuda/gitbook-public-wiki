---
description: A basic use of ike-scan with different command based scenarios
---

# IKE Scan

### Using to check for Main mode and aggressive mode:

```text
ike-scan 192.168.207.134
sudo ike-scan -A 192.168.207.134
sudo ike-scan -A 192.168.207.134 --id=myid -P192-168-207-134key
```

### Brute force:

```text
psk-crack -b 5 192-168-207-134key
Running in brute-force cracking mode
Brute force with 36 chars up to length 5 will take up to 60466176 iterations
```

```text
psk-crack -b 5 --charset="01233456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz" 192-168-207-134key
Running in brute-force cracking modde
Brute force with 63 chars up to length 5 will take up to 992436543 iterations
```

### Dictionary attack:

```text
$psk-crack -d /path/to/dictionary 192-168-207-134key
Running in dictionary cracking mode
no match found for MD5 hash 5c178d[SNIP]
Ending psk-crack: 14344876 iterations in 33.400 seconds (429483.14 iterations/sec)
```

