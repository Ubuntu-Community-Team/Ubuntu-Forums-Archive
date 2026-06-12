---
title: "Ubuntu 64 fails to respond"
date: 2004-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Xybr on 2004-11-20
I have this configuration:

Athlon 64 3200+
Shuttle AN50R (nVidia nForce3 150Gb)
ATi Radeon 9800 Pro
Sound Blaster Audigy-2 ZS
NEC ND-1300A DVD Burner (/dev/hdb)

/dev/hda - Maxtor 40GB (Spare drive - Ubuntu will be installed here)
/dev/hdc - My Windows XP drive
/dev/hdd - Data/Programs drive for Windows

I've reinstalled Ubuntu 64 several times and i get the same result.  Ubuntu 32 does not have this problem what so ever.

I install U64 and install files from the disc (i have tried using newer files from the web also).  Installation runs fine. 

I boot into U64 for the first time and it hangs due to an APIC issue, which every version of Linux i've tried has w/ my setup.  So I apply 'noapic' to the kernel args and it boots fine.

Now, X loads up GDM.  Sometimes it crashes here, sometimes it'll let me login.  When I can login, it shows the Gnome Splash window.  If I get past this part, then I'm welcomed w/ the desktop, except my mouse fails and everything appears to stop working.

I do not expect 3D to work until ATi decides to make AMD64 Linux drivers.  But I should at least get basic 2D functionality w/ the OSS drivers.  I've tried FC3 x86_64, I get the same problems. 

Any ideas on what is causing this?
If so, are there any fixes for this problem?

---

### Post by jdodson on 2004-11-22
i have heard of problem with the new ati 9800's, perhaps you should try and use the 32 bit ubuntu until 64 works.

---

### Post by Xybr on 2004-11-22
Ahh man.  Back to 32-bit then, I'll try it again whenever ATi releases their AMD64 drivers.  They say December.  We'll see.

---

### Post by mrmonaro on 2007-04-12
[http://ubuntuforums.org/showthread.php?p=2439466#post2439466](http://ubuntuforums.org/showthread.php?p=2439466#post2439466)

---

