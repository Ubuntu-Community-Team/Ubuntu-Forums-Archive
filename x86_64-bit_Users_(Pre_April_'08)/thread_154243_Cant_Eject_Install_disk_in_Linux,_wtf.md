---
title: "Cant Eject Install disk in Linux, wtf??"
date: 2006-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by UNIVSOUTHFLA on 2006-04-02
ok, now I just realized that I totally screwed up on my parition and need to reinstall OSX. Ok, when I try to eject the Linux install CD, I right click on the desktop icon for the CD, press Eject, and this error message comes up...
Unable to eject media
Show more details-
Umont:/dev/hbd mount disagrees with the fstab eject: unmount of `/tmp/disks-conf-hdb 'failed

---

### Post by aimislame15 on 2006-04-02
how about trying this... go to xterm (terminal window) and type

eject cdrom

if that doesnt work... hold down the mouse button or eject key (or both) at the same time during startup.. itll eject the cd.

---

### Post by jdp on 2006-04-02
If you just want to eject the disc, hold down the mouse button when you turn the Mac on.  It should eject after a short bit, then release the button.  Macs have had this feature since the first one. ;)

---

### Post by stmiller on 2006-04-02
Just type this in a terminal:

eject

---

### Post by plush on 2006-04-02
speaking of eject... do you guys know how to get the cd tray to close when you use the media button on the apple keyboard?  it opens fine with the button and even shows the nifty eject graphic, but it just won't close!  In xterm if I type "eject -t" when the tray is open it closes...  I read something about using eject-2.1.4 to fix this, but it  won't compile on my Powermac G5 :(  Any suggestions?

---

### Post by ssam on 2006-04-02
plush check if its been files as a bug, if not file it. [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

---

### Post by plush on 2006-04-02
I filed it.  Anyone know how I might go about fixing it?

---

