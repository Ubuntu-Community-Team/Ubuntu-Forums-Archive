---
title: "problems installing memory"
date: 2006-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by capitol on 2006-11-22
Hi

I just tried to install another 2 gb of memory in a dell 2850 to a total of 4 gb, the hw installation went smooth and the bios detected the new amount of memory.

The problem was that the machine went blank in the middle of the boot process, it might be a problem with gdm. I'll will continue to errorsearch this tomorrow but i wanted to check if there is someone else that have experienced the same problems.

I'm running dapper on that machine.

//Alex

---

### Post by RAOF on 2006-11-22
Have you tried running a memtest from the GRUB boot menu (or press "ESC" when it asks on booting)?  That's probably the first port of call.

---

### Post by capitol on 2006-11-23
I didn't run memtest as it was a shortage of time (production machine), but the bios memory check didn't find a problem (it's not nearly as good i know).

I removed gdm and the machine booted without problem, and is now running nice and steady with a load of around 2.5.

I'll report back if i experience any more memory related problems, it could of course be a bad pice of memory that isn't utilized right now.

---

### Post by RAOF on 2006-11-23
It's also possible that the AGP apeture lies within the address-space of the newly added memory?  That would either 1) make that part of your new memory unaccessable, or 2) kill any direct graphics write (as it would now be written to main memory, rather than the actual graphics card).

I'm not sure if 2) actually happens, but if memory problems persist, you may want to consider it.

---

### Post by tommyhot on 2007-02-02
I also have issues with my memory, I have 1.5GB RAM (1GB+512MB) and the system (Edgy Eft) hangs right after it reaches gdm login. It boots normaly only when I leave the 512MB one there. I didn't run memtest, but I ran Gold memory test and it didn't report any errors, so it's also probably gdm issue

---

### Post by Ocxic on 2007-02-02
Your kernel must be compiled with the option to support mor then 2GB of ram, I belive, (but don't know for sure), so you may need to manually re-compile your kerenel, but i could be wrong.

---

