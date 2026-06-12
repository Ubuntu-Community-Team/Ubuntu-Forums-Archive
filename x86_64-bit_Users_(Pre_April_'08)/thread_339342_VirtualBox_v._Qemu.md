---
title: "VirtualBox v. Qemu"
date: 2007-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-01-15
Having noticed that VirtualBox has gone open source under the GNU license, it looks very interesting. Still no 64-bit version, but perhaps that will come soon. Meantime, I have been been considering Qemu. Should I go ahead with Qemu, or wait for VirtualBox? What are the differences? Is there a synopsis showing capabilities of the two somewhere?

---

### Post by Enverex on 2007-01-19
Get VirtualBox. QEmu is a bit messy to set up where as VirtualBox has a nice GUI. VB also seems faster than QEmu. Both are free so just grab the Edgy .deb from the VB site.

---

### Post by Celil Rifat on 2007-02-06
kqemu just went open source. 

[http://fabrice.bellard.free.fr/qemu/index.html](http://fabrice.bellard.free.fr/qemu/index.html)

Looks exciting. I have not tried it yet, as I could not find any debian packages yet, but I hope they will be available soon. 

I am currently using VirtualBox, and eventhough  it looks great and works fine, it does not load in the new kernel 2.6.20. So if qemu does support the newest linux kernel, I might consider switching. Does anybody know if it would be possible to load my *.dvi images in qemu?

---

### Post by John Jason Jordan on 2007-02-06
> **Celil Rifat said:**
> kqemu just went open source. 
[http://fabrice.bellard.free.fr/qemu/index.html](http://fabrice.bellard.free.fr/qemu/index.html)
Looks exciting. I have not tried it yet, as I could not find any debian packages yet, but I hope they will be available soon. 
I am currently using VirtualBox, and eventhough  it looks great and works fine, it does not load in the new kernel 2.6.20. So if qemu does support the newest linux kernel, I might consider switching. Does anybody know if it would be possible to load my *.dvi images in qemu?
Since my original post I have found a local Linux guru who has been using Linux forever. He is a devotee of Vmware, and will hold my hand as I go through configuring it. My needs are simple, so Player is all I need. I have an unused XP license, although I will install 2000 instead. I'd rather use OSS, but I'm not adamant about it as some are.

---

### Post by Celil Rifat on 2007-02-07
> **John Jason Jordan said:**
> Since my original post I have found a local Linux guru who has been using Linux forever. He is a devotee of Vmware, and will hold my hand as I go through configuring it. My needs are simple, so Player is all I need. I have an unused XP license, although I will install 2000 instead. I'd rather use OSS, but I'm not adamant about it as some are.

I would recommend VirtualBox over VMWare. From my own experience VB is much faster. 

[http://www.virtualbox.org/](http://www.virtualbox.org/)

I was trying to switch to the alpha version of Ubuntu 7.04 but it appears that VirtualBox does not support Kernel 2.6.20 yet, that is the only complain I have about it, otherwise it works just great. It is very professionally done. 

I am excited about trying QEMU however, and I hope the Ubuntu repositories will be updated soon so that I can download it.

---

### Post by jbus on 2007-02-07
Virtualbox definitely seems to be faster than QEMU.

---

### Post by Celil Rifat on 2007-02-07
> **jbus said:**
> Virtualbox definitely seems to be faster than QEMU.

Have you tried the the accelerated version with kqemu?

---

### Post by in_flu_ence on 2007-02-09
I have used the VB on my laptop that has a widescreen. Somehow, it doesn't work well and got my windows distorted. I have yet to find a solution. BUt it works fine on my dekstop which is square:P

VMware is abit of a pain to install compared to VB. I would say both are running at about the same speed in my machine (in terms of getting the programme started and loading winXP).

---

