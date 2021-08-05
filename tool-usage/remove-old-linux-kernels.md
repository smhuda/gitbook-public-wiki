---
description: >-
  This guide will help you remove old and unused Linux kernels on your Ubuntu
  system.
---

# Remove Old Linux Kernels

By default, modern Linux versions keep the current kernel, plus one older version. However, in some instances, Linux doesn’t remove old versions of the kernel. One common problem of having old kernels is having an extensive list of bootable kernels on the GRUB \(boot\) menu.

## Display a List of Kernel Versions

To view a list of all kernel versions installed,  entering the following:

```text
sudo dpkg ––list | egrep –i ––color 'linux-image|linux-headers'
```

## Remove All Old Kernels Using the Command Line

The **apt** package manager can **automatically remove all old kernels**. To do so, run the command:

```text
sudo apt-get ––purge autoremove
```

The system scans for unused kernels and displays a summary of the files it wants to delete. It prompts you to confirm your choice to remove old kernels by pressing **`y`** and **Enter** to delete.

## All in 1 - One Liner

Searching and purging all old kernels can be acheived efficiently through a single line comprising of regular expression and some grepping and sedding s follows:

```text
echo $(dpkg --list | grep linux-image | awk '{ print $2 }' | sort -V | sed -n '/'`uname -r`'/q;p') $(dpkg --list | grep linux-headers | awk '{ print $2 }' | sort -V | sed -n '/'"$(uname -r | sed "s/\\([0-9.-]*\\)-\\([^0-9]\\+\\)/\\1/")"'/q;p') | xargs sudo apt-get -y purge
```

  

