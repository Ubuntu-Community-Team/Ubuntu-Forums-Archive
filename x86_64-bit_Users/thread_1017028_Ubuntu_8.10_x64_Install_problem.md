---
title: "Ubuntu 8.10 x64 Install problem"
date: 2008-12-20
forum: x86 64-bit Users
---

### Post by gvi70000 on 2008-12-20
Hello,
I need some help to install Ubuntu 8.10 PLEASE. I have a Q6600, Asus P5K Premium 4Gb Ram, nvidia 8800GTS 640Mb, 2x36Gb WD Raptor in RAID ) configuration and 2x WD250Gb on the same controller but they are not in raid.
I installed under Windows XP x64 Ubuntu on the second partition from the RAID but after restart i get (initramfs) and ....nothing. I've read some posts and they say it is because of SATA configuration in BIOS (should be configured as raid) but in my case is all ready configured. I try also the others start options and there i can see some errors (see the picture). Can any one help me to finish the install?

PS: When I've installed  Ubuntu 8.04 i had to edit menu.lst to change root (hd3,0) to  (hd something) to work, but in this situation i can't (don't know) how to edit menu.lst.

---

### Post by gvi70000 on 2008-12-22
any ideea?

---

### Post by Sef on 2008-12-24
How does the Live CD run?

---

### Post by gvi70000 on 2009-01-11
the cd is working fine. I use this tc to install Ubuntu on  two laptops and was ok. I think the problem is from RAID but i am not sure.

On 8.04 ia resolve the problem by editing menu.lst, now...i can't get there.

---

### Post by seamuso on 2009-01-11
Try booting with a noapic and see if you get past the errors .. the person in the following link was also having the same errors:

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-02/msg12283.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-02/msg12283.html)

---

### Post by Yellow Pasque on 2009-01-11
> On 8.04 ia resolve the problem by editing menu.lst, now...i can't get there.
Use a LiveCd to edit the menu.lst?

---

