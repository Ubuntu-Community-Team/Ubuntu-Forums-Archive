---
title: "Pismo installation woes"
date: 2006-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by bstone on 2006-05-12
I have a Powerbook G3 Pismo with an 80gb HD. It's partitioned into two parts- 60gb for OS X and another "LinuX" 20gb. OS X is installed on the 60gb and the 20gb is completely available.

I burned the 5.10 "Ubuntu_PowerPC_breezy" CD via Toast. Rebooted with C and nothing, so I did Option and saw the Ubuntu CD, selected it and was immediately dropped into Open Firmware with the options to "shut-down" or "mac-boot". Typing mac-boot didn't do anything but give me some cryptic "cache error". I ended up rebooting into OS X.

I'll try to reburn the ISO with FireStarter. Perhaps it was a bad burn. What else am I doing wrong?

---

### Post by 3rdalbum on 2006-05-12
I don't mean to insult your intelligence, but often the problem is that people try to burn the ISO as one file on a CD.

If you put the CD into the drive while OS X is running, is there just one file on it, or many files? If it's many files, you've burned it correctly. If it's just one file, you've done it wrong. You must use the "Disc Image" function of Toast (which is under the right-most button menu thingy).

If that doesn't help, try doing an MD5 checksum of the ISO file.

---

### Post by bstone on 2006-05-12
Many files. This is not my first linux install but it has proven the utterly most frustrating and difficult. I burned the ISO three different times with three different programs, checked the md5checksum (was correct) and nothing.

I am redownloading from a different mirror now and pray that helps.

---

### Post by jdp on 2006-05-12
Some older CD drives don't like discs burned at high speed.  Generally 8x or lower can help.

Do you have an upgraded CPU?  There could possibly be issues with the cache on it having causing trouble trying to boot the CD.  If it showed up in the Startup Manager (option boot menu) then you at least know you have a true NewWorld machine and don't need BootX.

---

### Post by bstone on 2006-05-14
[QUOTE=jdp]Some older CD drives don't like discs burned at high speed.  Generally 8x or lower can help.

Do you have an upgraded CPU?  There could possibly be issues with the cache on it having causing trouble trying to boot the CD.  If it showed up in the Startup Manager (option boot menu) then you at least know you have a true NewWorld machine and don't need BootX.[/QUOTE]

So I burned it at 1x. Same problem. C doesn't work, if I hold down Cmd-Opt-Shift-Del (which bypassed the primary disc for a secondary) I get this endless Open Firmware cache error. Can't read it as it goes too fast.

I know it's a NewWorld mac. I have installed other Linux distros on it before. For whatever reason Ubuntu doens't want to work, nor does Debian. I am becoming suspect it's my proc/mobo. Growl.....

---

