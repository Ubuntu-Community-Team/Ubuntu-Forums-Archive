---
title: "Problems with and old  g3 233mhz"
date: 2006-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by TGBre on 2006-02-11
I've been trying to install ubuntu on a old 233mhz g3 mac, but I can't get it to boot up and install. It has mac os 9. I've held "c" key down and it doesn't work. I've checked the forums, and I can't figure out what's wronge. I've tried re-burning the cd at different speeds and it doesn't work. Mac os 9 sees the cd but I can't get it to boot. I'm using nero 7 on my amd pc to burn it. I have no idea what to do. The mac was given to me and I don't want it to just take space in a closet. Someone please help me?

---

### Post by jdp on 2006-02-11
[http://www.applefritter.com/node/8936](http://www.applefritter.com/node/8936)
I'm assumign it's a Beige G3.  If it's an iMac it may need a factory made CD, or need to be burned on a "compatible" music CD-R.

---

### Post by TGBre on 2006-02-11
Thanks for the link. I'm going to try that!

---

### Post by TGBre on 2006-02-12
Now I'm having problems with bootx! I can't get it to work on the mac. I downloaded it on my AMD pc and burned a data disk with bootx on it. I've followed the instructions on what to copy, but it's not working. Need help? If anyone has an iso version of bootx, please send me a link? I want to get this old g3 up and running.

---

### Post by jdp on 2006-02-12
The first questions are: exactly which G3 is it, and what version of MacOS is it running?

---

### Post by TGBre on 2006-02-13
It's a Beige G3 and it has Mac OS 9 on it!

---

### Post by jdp on 2006-02-13
Ok, so you certainly do need BootX, as the Beige G3 is an OldWorld machine and won't boot Ubuntu directly, either from CD or HDD.  When you d/l the BootX file to your PC, are you leaving it in the original archive, or are you extracting the files and copying them over uncompressed?  If the latter, then just copy the whole original archive over.  PCs do bad things to the structure of MacOS executables, so it's best to leave all Mac archives that have anything more than plain data files as an archive.

Even a basic install of OS 9 should have the right software to open a regular Mac archive (.dmg, .sit, .hqx, .bin) as easy as double clicking the file.  One thing to watch is to be sure to put the file somewhere that has room for the expanded files.  If you have the file on a floppy and try to extract it, it will try to put the files on the floppy too, and run out of room really fast.  Copy to HDD first.

---

### Post by TGBre on 2006-02-13
Your not going to beleave this! I reburned bootx as an mac archive, and copy the files over and it can't unpack them. I beleave the person that had this mac before me tryed to clean everything off the system. Is there a way for me to wipe the hard drive then install ubuntu? Better yet, could I install mac os panther then install ubuntu on the drive with no resitance? (for course I would have to find a copy first!) I swear this mac is telling me that it's "the borg" and it's going to assimalate me! LOL!

---

### Post by 3rdalbum on 2006-02-13
Unfortunately, you can't run OS X Panther on the Oldworld. (Well, you can, but it's more difficult than getting Ubuntu going). I can't think of a way to get BootX onto the Mac if it doesn't have Stuffit Expander and you don't have another Mac around. You don't have a Mac OS 8 or 9 install CD? Some computers also come with a "restore" CD as well, which should do the trick too.

EDITED: Reminder to self: proof-read, and don't post while tired. Thanks to jdp for pointing out my silly mistake :-)

---

### Post by jdp on 2006-02-13
Try to find a program called **Stuffit Expander** on the HDD.  It should be in the **Applications** folder, but could be in something like **Internet Applications** folder, depending on which version of OS 9 is installed.

The maximum offially supported version of OS X is 10.2.8.  You can install 10.3 with the help of XPostFacto.  However, if you want to boot Linux, you will need an install of Classic Mac OS on there to run BootX.  It can't be done from OS X.  But, you can try to run Mac-On-Mac and run Ubuntu inside that while running OS X as the main OS.

The Beige G3 was the last desktop of the OldWorld Macs, and it has many quirks that make it more difficult to work with than anything from a B&W G3/iMac on up.

A clean install of OS 9 should include everything you need to get the archive unpacked, and even enough software to get on the internet and download BootX from the G3 on it's own.  OS 9 will include basic network software so that you can plug the G3 right into an ethernet hub and access a home network and it also includes Internet Explorer and Netscape that you can use to download BootX.

**EDIT:** and now that I see I've done a simu-post with 3rdalbum, I gotta mention that because the Beige is OldWorld, yu can't jsut erase the entire HDD and install with only Ubuntu.  That requires a B&W or iMac or better to work.

---

### Post by TGBre on 2006-02-15
Well It looks like I can't do anything intil I get a copy of mac os 9. The person that had this before me must of been parinod and deleted all the apps on the damn thing. I see it in the menu, but  it states, "can't find corresponding app" when I click on it. This sux for me! Oh well! But, I do want to thank you for all the help!

---

