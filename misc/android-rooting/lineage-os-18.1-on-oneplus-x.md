# Lineage OS 18.1 on OnePlus X

## Reference:

{% embed url="https://www.getdroidtips.com/lineage-os-17-oneplus-x/" %}

## Downloads:

* [LineageOS 18.1](https://drive.google.com/file/d/1CjP5fcLfrChWErnY0Dm1nomFrS\_DFeJw/view?usp=sharing)
* [Gapps](https://sourceforge.net/projects/opengapps/files/arm/test/20210130/)
* [Recovery - TWRP 3.2.3 14.02.2019](https://drive.google.com/file/d/1qx4JGFJG9UJO0ulDSI6a3hGtNF7dffdP/view?usp=sharing)
* [`https://twrp.me/oneplus/oneplusx.html`](https://twrp.me/oneplus/oneplusx.html)``

## Prerequisites

* First and foremost, create a [complete device backup.](https://www.getdroidtips.com/step-step-guide-backup-data-android-device/) This is because we will be wiping the data partition which will format your device.
* Next up, you will need to unlock the bootloader on your device. If you haven’t done so, refer to our guide on [How to Unlock the Bootloader on OnePlus X.](https://www.getdroidtips.com/unlock-bootloader-oneplus/)
* Once that is done, you must also have the [TWRP Recovery installed](https://twrp.me/oneplus/oneplusx.html).
* Also, [enable USB Debugging](https://www.getdroidtips.com/enable-usb-debugging/) on your device so that it gets recognized by your PC in the ADB Mode. For that, head over to Settings > About Phone > Tap on Build Number 7 times > Go back to Settings > System > Advanced > Developer Options > Enable USB Debugging.
* Next, up, download, and install the [Android SDK Platform Tool](https://www.getdroidtips.com/download-adb/) on your PC. This will provide you with the necessary binary files.
* Also, download and install the [OnePlus USB Drivers](https://www.getdroidtips.com/download-oneplus-usb-drivers/) onto your PC.
* Finally, download the Lineage OS 18.1 on OnePlus X: [Download Link](https://forum.xda-developers.com/t/lineageos-18-1-19-02-2021.4235865/)
* If you want Google Apps as well, then download the [Android 11 GApps](https://www.getdroidtips.com/download-android-11-gapps/) file

That’s it. You may now proceed with the installation steps.

#### Instructions to Install Lineage OS 18.1 on OnePlus X

1. Transfer the downloaded ROM and the GApps file to your device’s Internal Storage.
2. Now connect it to the PC via USB Cable. Make sure USB Debugging is enabled.
3. Head over to the platform-tools folder on your PC, type in CMD in the address, and hit Enter. This will launch the Command Prompt window.\
   ![cmd platform-tools](https://www.getdroidtips.com/wp-content/uploads/2020/06/cmd-platform-tools.jpg)
4.  Execute the below command in the CMD window to boot your device to TWRP Recovery

    ```
    adb reboot recovery
    ```
5. Then, select the System, Vendor, Data, and the Cache partition and perform a right swipe to format the selected partitions.
6. After this, go to the Install section of TWRP. Navigate to the downloaded LineageOS 18.1 ZIP file, select it and perform a right swipe to install it.
7. The process might take a few minutes. When the flashing is complete, go back to the Install section and this time select the GApps package. Perform a right swipe to install this file as well.
8. Likewise, you should also wipe the cache partition. You could either use the Wipe Cache button that would be available after flashing GApps. If not, then head over to Wipe, select the Cache partition and perform a right swipe to wipe it.
9. You may now reboot your device to the newly installed OS. For that, head over to Reboot and select System

