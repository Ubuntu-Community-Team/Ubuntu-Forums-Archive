---
title: "NDISWrapper with Broadcom 54g intermittently working"
date: 2005-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicholas on 2005-03-14
Hi,

I've installed Ubuntu 5.04 Preview amd64 version, and everything works fine except NDISWrapper 1.1 with the Broadcom 54g mini-pci in my laptop.

NDISWrapper installs fine, and it installs the broadcom windows 64 driver from the linuxant site fine too.

wlan0 is set as my default network interface, and it connects to my MSI RG54G2 wifi router with no problems.

I can browse the net for a minute or two, and then it just stops working.  I have to click deactivate in network admin tool and then click activate to get a working connection again.  This then lasts a few minutes, and then I have to go through the same process again, and again, and again............... :-o

32bit 5.04 with ndiswrapper and windows 32 driver works fine on the same laptop with none of the above problems.

It's very frustrating, can anyone help me out at all?

Regards,
Nik

---

### Post by Mastor on 2005-03-14
try le lastest cvs source

i had some problems with the "stable" release of ndiswrapper (10 seconds of running and then a kernel panic :( )
i don't know if will work because i've also updated the kernel at the same time..

---

### Post by Boomstickz on 2005-03-14
Hmm i'm running something similar to what you're running, except i'm not running a laptop, i'm running Ubuntu 64, with a MN-720 wireless card, the 5.04 Hoary Preview, and ndiswrapper 1.1. I have no problems, before I updated, and after I updated, since you have a laptop, what I would try to do is connect with ethernet, update ubuntu, get the latest kernel and stuff like that. Reason why I think this will fix it, is because of this.

I ran Fedora 3 64-bit and I have to say I was quite disappointed with it, problems all over the place, but I had the same problem you're stating, but I got it after I upgraded in Fedora 3, when I updated my kernel, so i'm guessing, its a conflict between your wireless card, and something in the kernel that may had been fixed. I'd give it a shot, tell us if that helps you at all.

---

### Post by jdong on 2005-03-14
How on earth are you emulating 32-bit Windows drivers in an AMD64 OS?

---

### Post by Boomstickz on 2005-03-14
We're not emulating 32-bit windows drivers, we're using the 64-bit broadcom wireless driver from Windows XP 64-Bit edition, Ndiswrapper 1.0 and above support that

---

### Post by nicholas on 2005-03-14
Thanks for your help everyone.

I was already up to date with synaptic updates including universe and multiverse.

I downloaded the latest cvs-snapshot source for ndiswrapper and it seems to have done the trick!  Downloads are quicker, and i haven't needed to restart the wireless inerface yet.

Thanks again.
Nik

---

### Post by Boomstickz on 2005-03-14
Awesome man, great to hear you up and running :)

---

