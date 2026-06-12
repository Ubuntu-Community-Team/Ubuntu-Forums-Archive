---
title: "ubuntu 7.04 amd64 running with intel E6420 and Asus P5b"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by ruiruas on 2007-06-07
Hi,
I've posted a message earlier saying I ouldn't install ubuntu on my new P5B motherboard...
But I've just made it!!! Thanks to a post where it explained that we need to blacklist the "intel_agp" module.

For anyone that doesn't know how, here it goes:

1.Use the alternate install CD for ubuntu 7.04 amd64 (it will recognize imediately the GigaB Onboard Lan - other common problem)

2. At the end of the instalation, DON'T LET THE MACHINE REBOOT. before that, press "GO BACK" and from the menu select the SHELL. in the shell, type:

    nano /target/etc/modprobe.d/blacklist

at the bottom of the file add

    blacklist intel_agp

then type "exit" to returnto the instalation menu.

Reboot and it will work (we hope) :-)

I'm now going to update and install nvidia drivers, etc. If I find anything interesting I'll get back to this.
Thanks to all for the excellent help we can get at the ubuntu forums.

---

### Post by capecove on 2007-06-07
Thanks for submitting that info. I don't have Intel based hardware any longer but I am sure there are those out there that do.

---

### Post by diafanos on 2007-06-11
I have a P5B Asus mobo and I had no problem installing Ubuntu since Edgy Eft (6.10). No need of alternative CD either.
I don't know if the problem is the cpu (i have an e6400), but I don't think so...

So, anyone who has this mobo, let's try installing Ubuntu with the usual procedure. If he/she is unlucky - as ruiruas was:( -, then follow his guide....

---

