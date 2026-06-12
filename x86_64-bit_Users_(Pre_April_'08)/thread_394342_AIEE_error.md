---
title: "AIEE error"
date: 2007-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by spelingchampeon on 2007-03-26
I have been trying to install 64bit desktop or server, off and on for the last couple of weeks. The installs all go great, but as soon as it reboots and starts, either it halts just before the desktop comes up, or the desktop login comes up, and as soon as I type something in, or move the mouse.. she locks. This happens with every version of 6.04 and 6.10 64bit, and with the live CD. Sometimes, when it locks up before the desktop starts, I get this, or something very much like it:

   [COLOR="DarkRed"]code: bad rip value
   rip [<ffffff0080246a907>] rsp <ffffffff8057de42>
  <0> Kernal Panic - Not Syncing: AIEE, Killing interrupt handler![/COLOR]

I have tested my memory with memtest86+ which ran for almost 3 hours with no errors. I have tried multiple HD's, and I have a also taken XP and installed it and had no issues whatsoever. I'm stumped to say the least. Any ideas?

MB: Gigabye GA-K8VM800M (rev 2.0) w- onboard video-lan-audio
CPU: AMD64 3400+
Memory: 1gig OCZ memory
HD: 80 gig WD

---

### Post by John Jason Jordan on 2007-03-26
> **spelingchampeon said:**
> ... I get this, or something very much like it:

   [COLOR="DarkRed"]code: bad rip value
   rip [<ffffff0080246a907>] rsp <ffffffff8057de42>
  <0> Kernal Panic - Not Syncing: AIEE, Killing interrupt handler![/COLOR]
When your computer just starts to boot and the Grub menu comes up, hit any key to stop it from continuing, then select the menu entry that is going to boot. Read the instructions at the bottom of the screen, i.e., hit e to edit the entry. On the second line of the entry add (one at a time):

noapic
pci=off

There are lot of other options to try as well, but start with those. Post back with the results or if my instructions were not clear. And meantime, it also wouldn't hurt to study up a bit on Grub, the Linux bootloader. Doing so would make it easier to understand adding boot options like the above.

---

