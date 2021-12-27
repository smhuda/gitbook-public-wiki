---
description: >-
  Nmap2CSV is a simple Python script to convert XML Nmap or Masscan output files
  to a single CSV spreadsheet which summarizes all hosts and open ports in a
  table
---

# Nmap2CSV

### **Usage:**

Pass the XML Nmap output \(`-oX`\) via a specified file or directory \(`-i`\). The resulted CSV spreadsheet is saved to a file \(default is nmap2csv-summary-tcp.csv\).

### **Options:**

```text
$ python nmap2csv.py -h
usage: nmap2csv.py [-h] [-i INPUT] [-p PREFIX] [-s SUFFIX] [-m MARKER]
```

### Script:

{% embed url="https://gist.github.com/smhuda/1deb2cf4c0e24d531e3651b421dc9c15" %}



### Disclaimer:

I do not own any part of this script and it is just shared here for reference.

