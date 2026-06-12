---
title: "AMD64 System Won't wake up from Hibernating"
date: 2006-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by mc413 on 2006-02-18
Hello all!

I have a Dekstop PC with an AMD64 processor and I'm trying to use the hibernate function. I've searched quite a bit on the Internet and ubuntu forums and followed some (mostly laptop-related) guidelines on how make it work. I tried all of them (including the noacpi line in GRUB's menu.lst and resume=my swap device) until i finally found a web page that said everyting I did was outdated and useless, but only had information on how to get hibernate working on a specific laptop.

Anyway, it all comes down to this. I select hibernate from Gnome's system menu, and it seems to work OK. I get an error "APIC Error on CPU0" somewhere in the middle of the process, but it seems to write the contents of the mem to disk OK. 

When I reboot, it does read the mem contents from the disk and then it either freezes or reboots, right after the last message which is:
[304.616739] swsusp: need to copy 20797 pages

I have 1GB of RAM and 1.5 GB Swap, Ubuntu 5.10, an AMD64 processor and a gigabyte motherboard.

Any ideas?

Thanks in advance!

---

### Post by mc413 on 2006-02-20
Still no ideas? Or at least a webpage with a how-to?

---

### Post by starkes on 2006-05-02
I'm having the same problem, only with different numbers and whatnot
i'm not using an amd64 though, im on a thinkpad r51 which is a 32bit pentium m

has anyone actually had hibernating work out of the box or is there an actual problem with ubuntu or something?

---

