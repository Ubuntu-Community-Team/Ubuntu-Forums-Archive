---
title: "FF704 amd64 bootup from cd freezes"
date: 2007-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Peter108 on 2007-08-25
Hello, all.

I recently installed FF704 server on an XP laptop, so have a bit of experience, but am still fairly noob.  

Yesterday, I downloaded and burned FF704 amd64, intending to a) run in live mode for awhile on my AMD64 laptop and b) eventually install.  I successfully ran both md5sum on the CD, then the CD integrity check from the main install menu.  However, when I try to boot, the boot dies after

```
* Configuring network interfaces... [OK]
```

Here are all the bootup messages

```
[* Loading kernel messages]
[mapping table messages]
* Loading hardware drivers
error receiving uevent msg: No buffer space available
firmware_helper [6242] main: error loading 'lib/firmware/bcm43xx_microcode5.fw'for device '/class/firmware/0000:03:00.0 with driver '(unknown)

[119.656521] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
[6324]main: error loading 'lib/firmware/bcm43xx_microcode5.fw'for device '/class/firmware/0000:03:00.0 with driver '(unknown)
[119.751603] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
[119.761283] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed
[6327]main: error loading 'lib/firmware/bcm43xx_microcode5.fw'for device '/class/firmware/0000:03:00.0 with driver '(unknown)
* Loading kernel modules ... [OK]
* Loading manual drivers ... [OK]
* Checking file systems...
fsck 1.40-WIP (14-Nov-2006) [OK]
* Mounting local filesystems ... [OK]
* Activating swapfile swap ... [OK]
* Configuring network interfaces ... [OK]

```

I actually left the machine on all night last night to see if it would advance beyond the above point.  It didn't.  I also tried FWIW, booting w/ and w/out the network cable plugged.  I'm aware that the bcm43xx stuff just means a little bit of work with ndiswrapper and such---but I can't get that far yet.

Attached is some system summary info describing from WinVista which may be useful. Thanks!
 
Compaq F572US

---

### Post by Kilz on 2007-08-25
Have you tried the alternate install cd. If you just want to install it is your best bet.

---

### Post by Peter108 on 2007-08-25
I'll give it a shot.  Thanks

---

### Post by Peter108 on 2007-08-25
Is there any way to boot to Gnome using the alt CD?  I really want to run FF for a time before committing to an install.

---

