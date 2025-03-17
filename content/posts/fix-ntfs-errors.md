---
title: "A half measure to treat NTFS errors"
date: 2023-05-08T13:10:14+01:00
draft: false

tags:
 - Tech
 - Idea
 - How-to
---
How do you correct when a drive is corrupted? Simply go to drive _Properties_, from  _Tools_ tab select the option to scan for errors and then use the dialogue that comes up if any error is found or, better yet, find the dialogue through your desktop notifications when you plug in your disk. But these are simply not possible on a Linux-based system if your filesystem of choice is NTFS.

# A little bit of background
When I had finally started using a portable harddisk as a backup, the then-existing Linux kernel module was of limited capacity and the go-to option had been a FUSE-based NTFS-3G driver which had its limitations. We have come a bit far since then. The current [NTFS3 driver](https://www.phoronix.com/news/NTFS3-For-Linux-5.15) since its being merged to the mainline kernel has made it easier to deal with the format but with one exception – fixing filesystem issues.

Sometimes a device would accidentally get removed while mounted or, like what happened recently, a file transfer to the disk during a kernel update can render the drive unmountable on Linux.

For a long time, my solution has been to borrow my dad’s work laptop for a day or go to a friend’s place to access a Windows computer. Perhaps at one or two occassions I even briefly had windows reinstalled on my main (and only) device just for this reason. But that changed when I discovered a better way to handle it.

# The Method
Instead of installing Windows, one could simply use the bootable drive to pass some simple bits of commands through the command prompt there to treat the drive.

## Basic Reqirements:
A Windows installer disk (or a writable disk along with a Windows Installer ISO to burn that image to create one; please refer to Step 0), a usable computer and, finally, the drive to fix.

## Steps:
The starting point is Step 1 unless a bootable installer needs to be created.

### Step 0:
[Download official images from Microsoft](https://www.microsoft.com/en-gb/software-download/) or grab a copy from any other source and burn it to a disk using a utility like `woeusb-ng` and this package is conveniently available [on AUR](https://aur.archlinux.org/packages/woeusb-ng).

Note: Be sure to disable to stop auto-mounting services like `udiskie` during the burn process.

### Step 1:
Boot using the installer disk (the key to press to get to boot selection page can be different depending on the OEM; for me it is the _Escape_ key). Connect the disk to fix (It can be done after Step 3 but this makes things simpler)

### Step 2:
After selecting the language the page with a _Install Now_ button at the centre will appear but choose _Repair Your Computer_ from the bottom-left side and select the _Troubleshoot_ option from the next page. There would be an option to open the _Command Prompt_.

### Step 3:
In the command prompt, first type `diskpart` and then `list volume` to get the assigned drive letter of the disk to be repaired.

Note: Pay extra attention to the details at the table in order not to  risk messing with the wrong disk.

Assuming that the volume letter is _C_, the thing to do now is to type `chkdsk \f C:` and that will both check the disk for errors and using the `/f` parameter means it will fix those too.

# Conclusion
This is what I have been using for the past couple of years. However, with the recent issue I first went to a free computer at my library but those have provisioning requring admin credentials to even conduct a scan which I do not have. The method then proved to be useful once again.
