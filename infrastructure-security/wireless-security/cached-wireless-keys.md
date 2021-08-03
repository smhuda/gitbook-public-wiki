---
description: >-
  A Powershell one liner to retrieve all the WiFi passwords stored on a
  computer:
---

# Cached Wireless Keys

### Windows:

```text
$a = netsh.exe wlan show profiles | Select-String -Pattern ": "; For ($i=1; $i -le $a.length * 2; $i+=2){ $b =  ($a -split "`t" -split ": ")[$i]; $c = netsh.exe wlan show profile name=$b key=clear | Select-String -Pattern "Key Content"; "Network: " + $b + $c}
```



