---
title: "Return of Double Clock Speed"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Orborde on 2005-10-14
[Original Hoary Problem and Fix Here](http://ubuntuforums.org/showthread.php?t=53094)

To paraphrase [Magical Trevor](http://www.weebls-stuff.com/toons/magical+trevor+2/)...
[i]It's back, and it's got a new trick
The Double Clock Speed Bug is ten times as slick
As the last time
The last time you saw it
Now you will see why we really abhor it.[/i]

So, I decided that 64-bit Ubuntu was too problematic, since nothing actually supports 64-bit yet, and rather than fiddle with 32-bit userlands and so forth, I decided to junk my somewhat damaged installation on my AMD64 laptop and install Breezy 32-bit. Well, the Double Clock Speed/50% CPU bug is back, and this time, it's harder to eradicate. Throwing no_timer_check, noapictimer, and noapic/nolapic all have the same effect: the problem is solved. Unfortunately, my network interface no longer works. D'oh! So I changed it back and have been living with double-speed clocks for the time being.

I'm using the k7 kernel, after installing the i386 distro and installing the k7 via Synaptic. Up-to-date Breezy and all that. So, help? :)

---

### Post by sfabel on 2005-10-14
Wait a sec - the "double clock speed" problem: is this happening on your 32-bit or on your AMD64 kernel?

Because this happens to me with the AMD64 kernel on a Athlon64 dual-core system.

Kernel parameter "notls" seemed to alleviate the effects a little, although I don't know about your network card.

Thanks,
Stephan

---

### Post by Orborde on 2005-10-14
[QUOTE=sfabel]Wait a sec - the "double clock speed" problem: is this happening on your 32-bit or on your AMD64 kernel?[/QUOTE]
I'm running the k7 (32-bit) kernel on an AMD64 CPU.

---

### Post by Aphorism on 2005-10-16
Have you tried the no_timer_check variable on the grub conf line?  Apparently the issue (at least for my mobo) stems from the IRQ double thumping the clock.  no_timer_check resolved this for my motherboard.

The amd64 bit port works great, and supports future advancements.  I would encourage you to use it and find work-arounds to your issues.  Both Flash and Java issues can be addressed through work around (either 64 bit open source alternatives or 32 bit chrooted proprietary format jails).

Good luck.

---

### Post by ThaRabbit on 2005-10-16
I'm fighting the same problem at the moment (CPU speed problems when using kernel 2.6.12.9 23 bit on a 64 bit AMD CPU), here's what I've found up until now:

The Ubuntu 5.10 final release uses the 2.6.12.9 kernel, the AMD K8 drivers required to autoscale the processor's speed (and hence solve this problem) is included in kernel revision 2.6.13.0 and higher. Sadly, there isn't a Ubuntu repository release of the 2.6.13.x kernel yet.

AMD provides the required powernowd-k8 files, but it will require recompiling the kernell from scratch based on the 2.6.13.x (I used 2.6.13.4) kernel sources. I keep running into a filesystem error with my kernel compiles, but I'll let you know when I've succeded.

The 64 bit release of ubuntu 5.10 final works a charm though :)

---

### Post by fox@epos.cz on 2005-10-16
I solved clock problem with noacpitimer kernel boot parametr (needs only for 32-bit version). It's problem of Acer 5024LWMi laptop.

---

