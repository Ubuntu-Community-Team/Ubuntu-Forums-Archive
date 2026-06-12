---
title: "Duelboot with OS9?"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by idumych on 2006-01-09
I would like to keep Mac OS9 installed because it plays DVDs really well on my Lombard. How I can accomplish a duelboot with OS9 and Ubuntu?

---

### Post by linear on 2006-01-09
Should be possible. This is just an outline, you should be able to find more details by a search of the forums.

First, back up! (If you don't want to risk data loss.)

Assuming you have only one partition on your hard disk currently, you will need to repartition - Ubuntu must be on a separate partition, and it should be the first partition. You can't do this with any Apple-supplied tool.

It's easier to start fresh and partition, leaving the first partition as free space. Install OS9 on the second partition.

Now install Ubuntu. Instructions here: [https://wiki.ubuntu.com/Installation/PowerPC](https://wiki.ubuntu.com/Installation/PowerPC)

Also read this: [https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot)

---

### Post by 3rdalbum on 2006-01-16
[QUOTE=linear]
Assuming you have only one partition on your hard disk currently, you will need to repartition - Ubuntu must be on a separate partition, and it should be the first partition. You can't do this with any Apple-supplied tool.[/QUOTE]

That sentence is a little unclear. Use Drive Setup to reformat your hard drive, but click on the "Custom Initialisation" button first. Put however much "unallocated" space at the beginning of the disk, then the partition(s) you will use for Mac OS.

Install Mac OS and then Ubuntu. There is an option in the Ubuntu installer to partition the biggest block of unallocated space - use that option.

Yaboot (the bootloader) will not automatically be set up to boot Mac OS. From what I've heard, it's possible to set it up to do so. If you want the computer to boot into Mac OS by default, follow these steps:

1. Install Ubuntu.
2. Boot the computer off a system CD.
3. Set up the Startup Disk control panel to boot up your Mac OS 9 partition on your hard drive.
4. Voila! It will boot into OS 9 by default. Whenever you want to startup Ubuntu, hold down Cmd-Opt-O-F while starting up, then type "boot hd:2,yaboot" at the OpenFirmware prompt. If that doesn't work, try higher numbers until it does. ("boot HD;3,yaboot" etc).

My father uses this computer as well, and he would get narky if he had to use a bootloader just to get into Mac OS, so that's how I keep him happy :-)

---

### Post by linear on 2006-01-17
[QUOTE=3rdalbum]That sentence is a little unclear.[/QUOTE]
Yes, I was summarizing too much.
> Yaboot (the bootloader) will not automatically be set up to boot Mac OS. From what I've heard, it's possible to set it up to do so. If you want the computer to boot into Mac OS by default, follow these steps:
But it's easier (even with other users who prefer Mac OS) to edit /etc/yaboot.conf and add the following line:
```
defaultos=macos  (or defaultos=macosx)
```
Also change the timeout on the menu to something shorter than the default 10 seconds:
```
timeout=30
```  (in tenths, so this is 3 seconds)

After saving edits, you must enter:
```
sudo ybin -v
```
to save changes to the boot partition.

No need to fiddle with Open Firmware each time you want to boot into Ubuntu.

---

