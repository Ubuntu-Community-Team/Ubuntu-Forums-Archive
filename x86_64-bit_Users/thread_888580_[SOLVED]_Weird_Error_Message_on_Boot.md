---
title: "[SOLVED] Weird Error Message on Boot"
date: 2008-08-13
forum: x86 64-bit Users
---

### Post by BrokenKingpin on 2008-08-13
I get the following error message on boot right before it hits the graphical loading screen:
&#8220;dmi_save_oem_strings_devices: out of memory&#8221;

Does anyone know what this error message is and how to fix it? My computer is a HP Pavilion m9250f running Ubuntu 8.04 dual booted with Windows Vista. I also notice Ubuntu sometimes hands on start-up, which I can resolve by power my machine totally off and leaving it for a couple minutes, could this be related to the error message. Any help on this issue would be great, thanks!

---

### Post by lukjad on 2008-08-13
Is your computer an HP?

I found an error at launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/236937").

An another link [here]("http://lkml.org/lkml/2007/12/18/361").

It seems as if you need a patch for the kernel. 

This is the last link that I am going to dumpon you:
[http://ubuntuforums.org/showthread.php?t=775237](http://ubuntuforums.org/showthread.php?t=775237)

Someone else will take it from here.

---

### Post by BrokenKingpin on 2008-09-10
I found those links as well, but I couldn't find the actual patch for the kernel. I may try upgrading Ubuntu to the latest stable kernel and see if that helps.

---

### Post by lukjad on 2008-09-10
Probably.

---

### Post by BrokenKingpin on 2008-09-14
[Solved] I installed Ubuntu 8.10 Alpha-5 64-bit (which uses the latest kernel) and everything works fine. I no longer get the kernel errors on startup and all freezing problems are gone.

---

### Post by lukjad on 2008-09-14
That's great. I'm waiting for that release to fix a lot of errors too.

---

