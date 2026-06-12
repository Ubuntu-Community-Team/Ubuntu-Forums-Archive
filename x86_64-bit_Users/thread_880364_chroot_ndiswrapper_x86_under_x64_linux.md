---
title: "chroot ndiswrapper x86 under x64 linux"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by Ptero-4 on 2008-08-04
Hi. I would like to know (since I got the POS realtek 8187b card) is it possible to "wrap" the x86 ndiswrapper in a chroot? A how?

---

### Post by Kilz on 2008-08-05
If you did, it would probably only work with applications in the chroot.

---

### Post by Ptero-4 on 2008-08-06
I know, but it´s the only way since there´s no native drivers and the winxp x64 ones won´t work at all (Damn, I really want a laptop that won´t look ugly, come with an ATI or S3 unichrome GPU or celeron/duron/via CPU, or with this stupid winwifi. But such thing is propably nonexistant or was made illegal by M$).

---

### Post by Jouke74 on 2008-08-06
A chroot of the ndiswrapper sounds like a recipe for disaster waiting to happen in my opinion, although I also think it is a very clever way to avoid 64 bit windows drivers. You need some 64 bit windows drivers for 64 bit ndiswrapper under a 64 bit system. Chroot might be a way around this, but I would love to see this work.

Another options is to buy a PMCIA card with wireless or USB wireless. Not something you want to hear either I know.

---

### Post by Ptero-4 on 2008-08-06
PCMCIA isn´t possible since the lappy came with ExpressCard/34. And USB external would be tricky since the stores here are under a rule that pretty much means "never tell your customer what chipset is in the cards that you sell". I guess my only option (other than going postal in the local M$ office) would be to dump my monthly quota (got 1024k the first 6GB and then goes down to 256k the rest of the month) getting the Sabayon 3.5 final x86 iso and hoping ndiswrapper doesn´t windoze my computer up as it does in the 3.5 beta 2 DVD I have.

Update: The kernel 2.6.27rc2 have a native driver for the rtl8187b (my hibernate is broken in that kernel though, dunno why since it used to work.)
Update2: Forgot that I had to get the /etc/issue file from a box running OpenSuSE 11.1 alpha release b4 being able to build the damn kernel (dunno why, it just bombs when I tried to compile if the openSuSE /etc/issue file isn´t there).

---

