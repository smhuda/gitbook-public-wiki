---
description: A guide to pulling APK files from an Android device
---

# Pulling APKs

### **Determine the package name of the app, e.g. "com.example.someapp". Skip this step if you already know the package name.**

```text
adb shell pm list packages
```

Look through the list of package names and try to find a match between the app in question and the package name. This is usually easy, but note that the package name can be completely unrelated to the app name. If you can't recognize the app from the list of package names, try finding the app in Google Play using a browser. The URL for an app in Google Play contains the package name.

### **Get the full pathname of the APK file for the desired package.**

```text
adb shell pm path com.example.someapp
```

### **The output will look something like:**

```text
package:/data/app/com.example.someapp-2.apk
package:/data/app/com.example.someapp-nfFSVxn_CTafgra3Fr_rXQ==/base.apk
```

### **Using the full pathname from Step 2, pull the APK file from the Android device to the development box.**

```text
adb pull /data/app/com.example.someapp-2.apk path/to/desired/destination
```

