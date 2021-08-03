# Android Application Testing

### Connect to Device/GenyMotion Virtual Device using ADB

**Install ADB \(Linux\):**

```text
sudo apt-get install android-tools-adb
```

**Windows:**

```text
<https://dl.google.com/android/repository/platform-tools-latest-windows.zip>
```

#### Retrieve the virtual device IP address. It is displayed on top of the virtual device window:

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b515b895-5c27-4422-a024-9edcac82cfa3/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b515b895-5c27-4422-a024-9edcac82cfa3/Untitled.png)

#### From another computer, open a command prompt and run:

```text
adb connect <virtual_device_IP>:5555
```

#### Find and Pull APK File:

Determine the package name of the app, e.g. "com.example.someapp". Skip this step if you already know the package name.

```text
adb shell pm list packages
```

Determine the package name of the app, e.g. "com.example.someapp". Skip this step if you already know the package name.

```text
adb shell pm list packages
```

Using the full path name from Step 2, pull the APK file from the Android device to the development box.

```text
adb pull /data/app/com.example.someapp-2.apk path/to/desired/destination
```

### Testing with Frida:

#### Install Frida on Windows/Linux:

```text
pip install frida
```

```text
pip install frida-tools
```

Make Sure GenyMotion is in **Bridged** mode and proxy is set to the Windows/Linux testing Machine IP and Port.

Install Frida Server on Mobile Device:

[https://github.com/frida/frida/releases/](https://github.com/frida/frida/releases/)

**frida-server-15.0.8-android-x86**

Copy Frida server file into the android phone tmp directory using adb push command as shown in fig. Here I have used Genymotion as an android emulator. After the copying the file change the permissions of the frida server files.

```text
adb push frida-server-downloaded /data/local/tmp/
```

Now go to ADB Shell and change permissions of Server file on the mobile device:

```text
adb shell
```

```text
cd /data/local/tmp
chmod 777 frida-server-downloaded

# Run the Frida Mobile Server
./frida-server-downloaded
```

Run Frida on Your Machine and Check for packages:

```text
frida-ps -Ua

OR 

frida-ps -U
```

### Using Frida Scripts:

```text
frida --codeshare pcipolloni/universal-android-ssl-pinning-bypass-with-frida -f com.testapp.app -U
```

```text
%resume
```

or use **No Pause** in script like:

```text
frida --no-pause --codeshare dzonerzy/fridantiroot -f YOUR_BINARY -U
```

#### Copy Pasting from Host to GenyMotion Emulator:

* **Long press the right click of your mouse until the paste sign appears**

