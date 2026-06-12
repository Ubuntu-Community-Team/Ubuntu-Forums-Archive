---
title: "AMD 64, Wrong Architecture problem, WiFi"
date: 2009-08-11
forum: x86 64-bit Users
---

### Post by brhokla on 2009-08-11
Hi,
I have a Gateway LT3103u series netbook that runs 2 gigs ram and a 250 gig HD. It uses an AMD Athlon64 and has the Atheros AR9285 wireless network adapter. 

I installed ubuntu on the computer and like all other users I can't get the WiFi to work. I am sure I installed the 64 bit version of the OS as the computer is a 64 bit processor and it is running great. I have tried installing the packets as recommended but when I try it tells me WRONG ARCHITECTURE "AMD64" and I can't install the packets like I need to in order to get the wifi to work. How do I tell which version 32 bit or 64 bit I have installed so I can verify that I am using a 64bit version of jaunty, my version of Jaunty is 9.04, Kernel 2.6.28-11-generic but I don't see anything saying its 64bit. I have tried installing

linux-image-2.6.28-13-generic
linux-backports-modules-2.6.28-13-generic
linux-backports-modules-jaunty-generic
linux-backports-modules-jaunty

All these are showing to be the amd64 download version...


I am having to do this off a USB drive as I can only access the web on the computer booted in windows vista. Thanks for any help....

---

### Post by mikewhatever on 2009-08-12
Use **uname -m** command. If the output is i86_64, you have a 64bit version.
Could it be that Athros only makes 32bit packages?

---

### Post by lensman3 on 2009-08-12
From a command line do:

"more /proc/cpu*"

It will tell you exactly what CPU is installed.

---

### Post by Yellow Pasque on 2009-08-12
You probably installed 32-bit Ubuntu.

> It will tell you exactly what CPU is installed.
The user seems certain his/her CPU is AMD64, so I don't think that's helpful in this case.

> I am sure I installed the 64 bit version of the OS as the computer is a 64 bit processor and it is running great.
32-bit would run well too, so that doesn't mean you installed the 64-bit version of Ubuntu.

> I have tried installing the packets as recommended
As recommended by what? Please link to whatever guide you're following.

---

### Post by undershepherd1 on 2009-08-12
I have an AMD 64 Athlon x2 Acer laptop. I use WiCD for Ubuntu 9.04 and it works great.

---

### Post by Thelasko on 2009-08-13
How are you installing them?  Are you using the [repositories]("http://www.psychocats.net/ubuntu/installingsoftware")?

---

