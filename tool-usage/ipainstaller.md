---
description: A tool to pull IPA files from an iOS device
---

# Ipainstaller

Since you have a jailbroken iOS device, try installing ipainstaller from Cydia and then use

ipainstaller to extract the app to an .ipa file. Use the following to list all the apps installed on my jailbroken device and grab the bundle id of that app you wish to extract.

### List of IPAs installed:

```text
ipainstaller -l
```

### Extract it using:

```text

ipainstaller -b <app_bundle>
ssh root@mobiledeviceip
password: alpine
```

