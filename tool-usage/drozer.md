---
description: An installation and wiki guide to using Drozer for Android application testing
---

# Drozer

## Setup:

**Install missing dependency**

```text
sudo apt install -f
dozer
adb forward tcp:31415 tcp:31415
drozer console connect
```

Once your emulator is up and running, it is now time to have some sideloading fun. The folks at MWR labs have created an awesome Android attack framework called “drozer”. The framework consists of software that needs to be installed on Ubuntu, as well as an “APK” file that needs to be sideloaded onto your emulated Android.

First, you need to download both the “Ubuntu/Debian” package, and the drozer Agent APK files from MWR labs. The following screenshots show what you are looking for:

### Debian/Ubuntu Package - Drozer Agent APK file

After the downloads are complete, perform the Ubuntu/Debian package installation first, as follows:

```text
$ sudo dpkg -i ~/Downloads/drozer_2.3.4.deb
```

```text
$ sudo apt install -f
```

Seriously? It’s that simple? Yes! This will nicely install all of the required dependencies for you. It seems a little backwards, and counterintuitive, but trust me, this will work well.

### Side-Loading the Drozer Agent APK

Now it’s time to use our Android emulator to sideload the drozer APK package. In addition to this, if we have another APK we want to perform penetration testing against, we probably want to sideload that APK file as well.

The first steps are to make sure your emulator is running, check access with ADB, and sideload packages as needed.

```text
$ emulator -avd pentest1 & $ adb devices
```

### List of devices attached

```text

$ adb install ~/Downloads/drozer-agent-2.3.4.apk
```

### Drozer Agent Installed

In order to use “drozer”, we must start the agent App on the Android emulator, and then turn on the embedded server, which listens on TCP port 31415. In addition to this, we must use “ADB” to forward the TCP port 31415 to the Android emulator so that we may communicate between the Ubuntu host and the Android drozer Agent. After forwarding the TCP communications, use the “drozer” command under Ubuntu to connect to the drozer console.

### Connecting to the Drozer Console

At this stage, we have a fully operating attack framework, and can use many of the reconnaissance, scanning, and attack commands that drozer provides for us. The example below simply lists Android packages on the system.

The various drozer modules have appropriate help associated with each. From a penetration testing perspective, you should treat this like any other penetration testing activity, meaning you need to perform reconnaissance, APK package information gathering of various providers, intents, broadcast receivers and so forth before starting to exploit some of the inherent weaknesses.

```text
$ sudo dpkg -i ~/Downloads/drozer_2.3.4.deb
$ sudo apt install -f
$ emulator -avd pentest1 &
$ adb devices
$ adb install ~/Downloads/drozer-agent-2.3.4.apk
```

## Testing:

### Find out the list of applications using keywords:

```text
dz > run app.package.list -f MyApplication (or any other app name)
```

### Run a vulnerable activity from the package:

```text
dz> run app.activity.start --component com.mobile.app ExponentDevActivity
```

### Find out exported activities:

```text
dz> run app.activity.info -a com.mobile.app
```

### Find out package information:

```text
dz> run app.package.info -a com.mobile.application
```

### Attack Surfaces:

```text
dz> run app.package.attacksurface com.mobile.application
```

### Find URIs

```text
dz> run scanner.provider.finduris -a ie.mobile.application
```

