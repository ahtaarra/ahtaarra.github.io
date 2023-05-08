---
title: "A half measure to correct NTFS errors"
date: 2023-05-08T13:10:14+01:00
tags:
 - Tech
 - Idea
 - How-to
draft: false
---
# A little bit of background
When I had finally started using a portable harddisk as a backup, the then-existing Linux kernel module was of limited capacity and the go-to option had been a FUSE-based NTFS-3G driver which had its limitations. We have come a bit far since then.

The current [NTFS3 driver](https://www.phoronix.com/news/NTFS3-For-Linux-5.15) since its being merged to the mainline kernel has made it easier to deal with the format but with one exception – fixing filesystem issues.

Sometimes a device would accidentally get removed while mounted or, like what happened recently, a file transfer to the disk during a kernel update can render the drive unmountable on Linux.

For a long time, my solution has been to borrow my dad’s work laptop for a day or go to a friend’s place to access a Windows computer. Perhaps at one or two occassions I even briefly had windows reinstalled on my main (and only) device just for this reason. But that changed when I discovered a better way to handle it.

# The Method
Instead of installing Windows, one could simply use the bootable drive to pass some simple bits of commands through the command prompt there to treat the drive.

## Basic Reqirements:

A Windows installer disk (or a writable disk along with a Windows Installer ISO to burn that image to create one), a usable computer and, finally, the drive to fix.

## Steps:

### Step 1:
[Download ISO](https://www.microsoft.com/en-gb/software-download/) and burn it on a disk using a something like `woeusb-ng` and you may find one of its packages [on AUR](https://aur.archlinux.org/packages/woeusb-ng) convenient if you use an Arch-based distro.

Note: Be sure to disable to stop auto-mounting services like `udiskie` during the burn process.

### Step 2:
Boot using the installer disk (the key to press can be different depending on the OEM; for me boot drive selection is the _Escape_ key). Connect the disk to fix (It can be done after Step 3 but this makes things simpler)

### Step 3:
After selecting the language the page with a ‘Install Now’ button at the centre will appear but choose the ‘Repair Your Computer’ option at the bottom-left corner and select the ‘Troubleshoot’ option from the next page. There would be an option to open the ‘Command Prompt’.

### Step 4:
In the command prompt, first type `diskpart` and then `list volume` to get the assigned drive letter of the disk to be repaired.

Note: Pay extra attention to the details at the table in order not to  risk messing with the wrong disk.

Assuming that the volume letter is C, thing to do is to type `chkdsk \f C:` and that will both check the disk for errors and using the `/f` parameter means it will fix those too.
# Conclusion
This is what I have been using for the past couple of years. However, with the recent issue I first went to a free computer at my library but those have provisioning requring admin credentials to even conduct a scan which I do not have. I again solved my problem using this method.
