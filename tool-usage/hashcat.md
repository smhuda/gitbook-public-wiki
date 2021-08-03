---
description: >-
  Hashcat is a password recovery and cracking tool. This is a quick go-to
  command wiki for it, although you should check the hashcat manual for
  extensive usage.
---

# Hashcat

## Hashcat WPA Wireless Rule-based

```text
hashcat.exe -m 2500 -r rules/best64.rule capture.hccapx rockyou.txt
hashcat.exe -m 2500 -r rules/best64.rule capture.hccapx rockyou.txt
```

### WPA Wireless Bruteforce

```text
hashcat.exe -m 2500 -a3 capture.hccapx ?d?d?d?d?d?d?d?d
```

### cap to hccapx convert

```text
git clone <https://github.com/hashcat/hashcat-utils>
cd src
make
cap2hccapx.bin input.cap output.hccapx
```

### WPA Dictionary

```text
hashcat.exe -m 2500 capture.hccapx rockyou.txt
```

## NTLMv2

```text
hashcat -m 5600 -r rules\\myrules.rule hash1.txt rockyout.txt --force
```

