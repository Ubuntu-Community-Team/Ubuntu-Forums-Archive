---
title: "automount and usb drives"
date: 2005-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by rquint on 2005-11-15
I'm having trouble with automount and usb drives (an external Zip drive and a 512 MB flash drive).  Although both drives show up in "Places|Computer" when plugged in and disappear when physically unplugged and all the automount options are checked in "Desktop|Preferences|Removable Storage", automount doesn't work.

lsusb reports both drives are there when plugged in.  I can manually mount and unmount them if I create the proper folders in /media, but then I get a new icon in "Places|Computer" even if I use exactly the same name as shown when I plug in the drive .  Automount works with my CD drive.  HAL and D-Bus are installed.  I'm at a loss.

I'm never sure whether a problem like this is a general Gome-Ubuntu problem or specific to the powerpc.  I'm running Breezy on a 500MHz translucent plastic case iMac.

---

### Post by khc on 2005-11-15
In System->preference->Removable drives and media, is "mount removable drives when hot-plugged" checked?

---

### Post by rquint on 2005-11-16
Yes, System->preference->Removable drives and media, "mount removable drives when hot-plugged" is checked.  I've also tried playing with pmount.allow and if there is an entry there-e.g., /dev/sda4, and only the zip drive is plugged I can insert a disk and it is mounted, but that means including all possible combinations of all usb devices in every order they could be connected.  Furthermore, in this case device is mounted as sda4 even though there is still the icon for External Zip Drive in "Places|Computer".

---

### Post by ssam on 2005-11-17
does anything show up in dmesg when you plug them in?

do you have any odd file systems on the disks. could you reform one of the disks as ext2/3 or fat?

---

### Post by rquint on 2005-11-23
After some experimentation (and following some hints in a couple other forums) I updated pmount, dbus and hal to the newer versions that exist in archive.ubuntu.com/pool/main rather than the ones synaptic reports as the latest version.  That has solved my problem with automount.

---

