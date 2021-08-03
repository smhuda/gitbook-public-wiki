---
description: A short wiki of Nmap scripts and tricks to use on different scenarios
---

# Nmap

### Clickjacking Script

```text
sudo nmap --script clickjacking-prevent-check -Pn -p 443 www.example.com -oN NmapClickJacking.txt
```

### DNS Cache Snooping

```text
sudo nmap -sU -p 53 --script dns-cache-snoop.nse --script-args 'dns-cache-snoop.mode=timed,dns-cache-snoop.domains={www.google.com}' 192.168.1.253-
```

### Greppable Output

```text
sudo nmap -PER -sn 192.168.1.0/24 -oG - | awk '/Up$/{print $2}
```

```text
nmap -n -sn 192.0.2.0/24 -oG - | awk '/Up$/{print $2}'
```

### Internal IP Leak

```text
nmap --script http-internal-ip-disclosure -oN NmapIPLeak.txt www.example.com
```

### Terminal Services RDP

```text
sudo nmap -p3389 --script rdp-enum-encryption 192.168.0.1
```

### Default Credential Scanning:

```text
nmap -p80 --script http-default-accounts host/ip
```

**Could add common web ports above as follows:**

`66,80,81,443,445,457,1080,1100,1241,1352,1433,1434,1521,1944,2301,3128,3306,4000,4001,4002,4100,4433,5000,5432,5800,5801,5802,6346,6347,7001,7002,8008,8080,8443,8888,30821`

### Telnet

```text
sudo nmap -p23 192.168.9.232 --script telnet-encryption
```

### Host Discovery

```text
nmap -sn 10.0.0.0/24 -oN output.txt
nmap -Pn 10.0.0.0/24 -oN output.txt (no Ping scan)
```

### TCP Scan

### All ports All Scripts \(use sSV for version detection\)

```text
nmap -iL Desktop/desktopstargets -sS -p 0-65535 -A --min-rate=2000 -oN Desktop/desktops_tcp_script --stats-every 10s
```

### Top 1000 ports

```text
nmap -sSV -iL hostlist.txt -oN TCPTop100VersionScan.txt
```

### UDP Scan Top 1000

```text
nmap -sU -iL hostlist.txt -oN UDPTop1000Scan.txt --max-rtt-timeout=220ms --max-retries 0
```

### UDP All ports

```text
nmap -sU -iL hostlist.txt -p0-65535 -oN UDPTop1000Scan.txt --max-rtt-timeout=220ms --max-retries 0
```

### Find Hosts

```text
sudo nmap -PER -sn 192.168.93.0/24 -oG - | awk '/Up$/{print $2}'
```

```text
nmap -PER -sn 172.16.10.0/24 (find live hosts on an ip range)
nmap -sn 10.0.0.0/24 –oN file (ping scan )
```

```text
nmap -Pn 10.0.0.0/24 –oN file (no ping)
Sometimes shown as -P0 (Zero)
arp-scan 10.0.0.0/24 - arp cant get passed routers
nmap -sP 10.0.0.0/24- arp cant get passed routers
ettercap - arp cant get passed routers
```

### Find Services

```text
nmap -sSV -p0-65535 -oN text.txt 10.0.0.1 --script=banner
nmap -sUV -p0-65535 1--script=ssl*,tls*0.0.0.5 --max-rtt-timeout=250ms --max-retries 0 -oN file
ncat –v –n –t –w 10.0.0.1 1-100
nmap -iL text.txt
nmap –O 10.0.0.1 (os scan
--script=ssl*,tls* (ssl and tls scripts)
```

### IP or File Exclusion

```text
--excludefile <filename> (for exluding list of ip's in a file)
--exclude <ip> for 1 ip
```

### Scripts

```text
nmap -> scripts
find / -name *.nse 2>/dev/null
or
updatedb
locate *.nse
```

### NFS Share

```text
nmap -sV --script=nfs-showmount
```

### LDAP Port 389

```text
$ nmap -p389 --script ldap-rootdse 10.0.0.1
```

### Nmap HTML Output Conversion

```text
nmap -A -oX nmapoutput -T5 192.168.0.1
xsltproc nmapoutput.xml -o scanme.html
```

### **Nmap Timing Template**

As we have seen that Nmap has multiple timing templates that can be used differently as according to the requirement. Click [here](https://www.hackingarticles.in/understanding-guide-nmap-timing-scan-firewall-bypass/) to check the timing scan article. Let’s see what’s inside the timing template. to get the description of timing template we’ll use **-d** attribute.

```text
nmap -T4 –d -p21-25 192.168.1.139
```

#### **Maximum Retries \(–max-retries\)**

–max-retries specifies the number of times a packet is to be resent on a port to check if it is open or closed. If –max-retries is set to 0, the packets will be sent only once on a port and no retries will be done.

```text
nmap -p21-25 192.168.1.139 --max-retries 0
```

#### H**ost-timeout**

The **–host-timeout** is an attribute that specifies the scan to give up on a host after the specified time. The lesser the time specified the more are the chances of inaccuracy in scan results.

We can specify the time in milliseconds \(**ms**\), seconds \(**s**\), minutes \(**m**\)

```text
nmap -p21-25 192.168.1.139 --host-timeout 100ms
```

#### **Hostgroup**

The host group attribute is specified to scan a specified number of hosts in the network at a time. You need to specify the minimum number of hosts or maximum number of hosts or both to be scanned at a time

```text
nmap -sP 192.168.1.1/24 --min-hostgroup 3 --max-hostgroup 3
```

#### **Maximum rate \(max-rate\)**

Rate is an attribute that specifies at what rate is the packets are to be sent, in other words, number of packets to be sent at a time. Max-rate specifies the maximum number of packets to be sent at once.

```text
nmap -p21-25 192.168.1.139 --max-rate 2
```

#### **Minimum rate \(min-rate\)**

Min-rate specifies the maximum number of packets to be sent at once. Here if we want at least 2 packets must be sent on target’s network at the same time not less than this, then need to execute below command.

```text
nmap -p21-25 192.168.1.139 --min-rate 2
```

#### **Parallelism**

Parallelism attribute is used to send multiple packets in parallel, min-parallelism means that the number of packets to be sent in parallel is to be greater than the value specified and max-parallelism means that the number of packets to be sent in parallel is to be less than or equal to the value specified

```text
nmap -p21-25 192.168.1.139 --min-parallelism 2 --max-parallelism 2
```

#### **Max-rtt-timeout**

max-rtt-timeout specifies the maximum value of time that is to be taken by a packet to return a reply

```text
nmap -p21-25 192.168.1.139 --max-rtt-timeout 50ms
```

#### Output Live Machines on a network with Nmap

```text
nmap -n -sn 192.0.2.0/24 -oG - | awk '/Up$/{print $2}'
```

During the Red Team Operations, It is sometimes benifitial to monitor the dynamic nature of the client's Infrastructure. As a intial scan we can use nmap to monitor Network State in a short period of time gap and check if any specific port changes accordingly. We can simply use a small bash script for that. You can also modify this script as per your requirement. 

### RAW Bash Script

{% code title="nmap-diffing.sh" %}
```text
#!/bin/bash
mkdir /Nmap-Diffing/
d=$(date +%Y-%m-%d)
y=$(date -d yesterday +%Y-%m-%d)
/usr/bin/nmap -Pn -A -sV --max-retries 1 --max-scan-delay 20 --defeat-rst-ratelimit -T4 -p1-65535 -oX /Nmap-Diffing/scan_$d.xml 192.168.0.1/24 > /dev/null 2>&1
if [ -e /opt/nmap_diff/scan_$y.xml ]; then
	/usr/bin/ndiff /Nmap-Diffing/scan_$y.xml /Nmap-Diffing/scan_$d.xml > /Nmap-Diffing/diff.txt 
fi
```
{% endcode %}

### Setting up Cron

We can also set up a cron job and redirect logs to a file for our reference by adding cron job as below

{% code title="crontab -e" %}
```text
0 9 * * * /THP/Recon/nmap-diffing.sh >> /var/log/demowebsite.log 2>&1
```
{% endcode %}

This is a very basic script that runs nmap every day using default ports and then uses ndiff to compare the results. We can then take the output of this script and use it to notify our team of new ports discovered daily.

