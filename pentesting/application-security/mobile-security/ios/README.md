# iOS Application Testing

#### Jailbreaking iOS Device:

[https://checkra.in/](https://checkra.in/)

After iOS Device is Jailbroken, Cydia is installed on the device. This can be used to install multiple testing tools like:

* MTerminal
* IPA Installer
* Frida Server

#### Installing SSL Kill Switch 2:

```text
Sequrus-iPad:~ root# wget <https://github.com/nabla-c0d3/ssl-kill-switch2/releases/download/0.14/com.nablac0d3.sslkillswitch2_0.14.debSequrus-iPad:~> root# dpkg --install com.nablac0d3.sslkillswitch2_0.14.deb
```

```text
Sequrus-iPad:~ root# dpkg --install com.nablac0d3.sslkillswitch2_0.14.deb
```

```text
Sequrus-iPad:~ root# killall -HUP SpringBoard
```

Now SSL Kill Switch 2 will appear in Settings, you just need to toggle it on!

### Pulling IPA from iOS Device:

```text
Sequrus-iPad:~ root# ipainstaller -l
```

```text
Sequrus-iPad:~ root# ipainstaller -b <package-name>
The application has been backed up as /private/var/mobile/Documents/Package-Name.ipa.
```

Now Connect to the iOS Device IP address using FileZilla to download the IPA from the above Location. This IPA can be used on tools like MobSF for static analysis

### Frida on iOS:

If Frida Server doesn't start through Cydia, Start is manually:

```text
Sequrus-iPad:/usr/bin root# frida-server -l 192.168.0.135
```

#### List devices:

```text
C:\\Users\\sequr>frida-ls-devices
```

#### List Installed Applications:

```text
frida-ps -Uai
```

#### Connect to the iOS Device Using USB:

```text
C:\\Users\\sequr>frida-ps -Ua
Waiting for USB device to appear...
```

#### Connect to the iOS Device Remotely Using its IP Address:

```text
C:\\Users\\sequr>frida-ps -H 192.168.0.135
```

#### Using a Codeshare Script via USB Connection:

```text
C:\\Users\\sequr>frida --codeshare federicodotta/ios13-pinning-bypass -f <package-name> --no-pause -Ua
```

#### using Codeshare Script via Remote IP Connection:

```text
C:\\Users\\sequr>frida --codeshare federicodotta/ios13-pinning-bypass -f <package-name> --no-pause -H 192.168.0.135
```

### Troubleshooting:

#### Unable to connect to remote frida-server / Waiting for USB device to appear...

#### Server Side - On iOS Device by SSH-ing to the device

```text
/usr/bin/frida-server -l <iOS Device IP Address>
```

#### Client side - on Testing Machine with Frida:

```text
frida-ps -H <iOS Device IP Address>
```

