---
title: "Hang on Installation / X Startup"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by rob13s on 2006-06-10
Hi -

I've got a fairly vanilla Athlon64 3400 / nforce 3 system, and I'm attempting to install 6.06 AMD64 on from the live cd. Everything seems to go ok until X starts up. I get the mouse, the status splash screen box, and the startup sound begins to play. Almost instantly, the sound starts breaking up, the system locks (no response from the mouse or any keys), and I'm done.

One thing I find interesting is that my system is now useless until I cycle power. If I simply reset, there's chaos - Windows crashes while booting and keeps resetting, even booting off the x86 6.06 live CD (which normally works fine) leads to kernel panics. If I power cycle the system, everything works fine.

This is rock solid system - I've used it for heavily for development under windows and under Ubuntu 5. 6.06 x86 works fine. 6.06 AMD64 really hurts it badly.

Other recent AMD64 distributions have no problem (e.g. Gentoo). 

Any advice? Thanks!

---

### Post by daniel.santos@pobox.com on 2006-06-14
Exact same problem here, except that my sound doesn't break up (the startup sound).  This hang occurs immediately after the sound finishes playing.  I used another LiveCD to look at the log and the only thing of note was that irdad crashed seconds before the last message to the log file.  I yanked a bunch of stuff out of init.d to see if I could absolve this issue, but to no use (one of which was bluez, thinking that my irda driver was getting loaded as a dependency of that, but I'm a n00b on this).

This happens both after installing (if I use the text mode install) and when attempting to use the LiveCD.  I will follow up with more complete system info as soon as I figure out a descent way to dump all of that (any suggestions?).  But it's basically this:

* Athlon 64 3000+
* nForce 4 chipset
* Promise FastTrak S150 SX4-M (but it died when I booted with it removed from the machine)
* motherboard has build-in AC-95 sound, but I have it disabled in the BIOS
* I also have the nvidia raid disabled in the bios
* Create Labs SB Live! Gold (the original PCI one, I paid a lot for it some time back :)
* nVidia GeForce 6800 Ultra video card (the massive power-sucking kind)
* some type of 40 GB Maxtor hard drive (this is what I installed it on.  I have 2 other drives that are attached to the raid card, but like I said, it crashed with those drives and the raid card completely disconnected from the machine)
* LITE-ON DVDRW LDW-451S (DVD burner)
* Alesis ADATEdit card (an 8-track audio device, Note that the install didn't find a driver for it, which I didn't expect it to)

Daniel

---

### Post by mooshie on 2006-06-16
Hello,

A week ago I began installing Ubuntu onto my 3700+ AMD 64 with Ubuntu LTS. I had a lot of problems with this version, including the CPU "soft locking" on boot. After a couple days of frustration I installed 5.10, and then upgraded to 6.06 (I did this using the system upgrade tool/apt-get, NOT the CD). Everything works fine now.. have you tried doing this?

Nate

---

### Post by sgornick on 2006-09-27
I am experiencing a problem that is possibly related -- on startup, gnome hangs as soon as it hits the attempt to play sound.  

I notice that when it is hung, I can switch to a virtual console (Ctrl-Alt-F1) and do a ps to find that there are two instances of esd spawned.  If I kill the first instance, then gnome resumes in loading the desktop no problem.

As a workaround, I disabled the system sound for Log in and then I can start up and have no sound problems thereafter. 

Is your problem possibly a result of the esd jam as well?
 
[http://www.ubuntuforums.org/showthread.php?t=248166&highlight=sound+power+startup](http://www.ubuntuforums.org/showthread.php?t=248166&highlight=sound+power+startup)

---

