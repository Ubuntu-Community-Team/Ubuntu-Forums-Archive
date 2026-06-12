---
title: "Finally, Ubuntu on an Abit K8VPro"
date: 2004-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Baloo on 2004-11-02
Ok after a lot of messing about I finally got Ubuntu installed on my Abit K8VPro. Problems I encountered :-

On board nic isn't recognised. - Had to install a PCI nic to get the network started.

VIA velocity driver supplied kernel panics on loading right after hotpluging is enabled. - Had to disable the onboard nic in the bios.

Other than that it's all running sweet now :)

---

### Post by latrine on 2004-11-02
Ok... Just did it too..precious tip... I will update the bug in bugzilla

IT IS VERY GOOOOOOODLOOKING... :) let's see if I can mess it up installing Ndiwrapper and connecting to the internet!! :)

---

### Post by Baloo on 2004-11-02
Now if only I can get mono/f-spot/tomboy working.

---

### Post by Medah on 2004-11-03
[QUOTE=Baloo]Ok after a lot of messing about I finally got Ubuntu installed on my Abit K8VPro. Problems I encountered :-

On board nic isn't recognised. - Had to install a PCI nic to get the network started.

VIA velocity driver supplied kernel panics on loading right after hotpluging is enabled. - Had to disable the onboard nic in the bios.

Other than that it's all running sweet now :)[/QUOTE]
 Do you know what nic is onboard? I have an Abit KV8-MAX3 with 3com 59x card, using the sk98lin driver. I usually have to modprobe this driver manually, altough i cant remember if i did on ubuntu.

---

### Post by Baloo on 2004-11-03
[QUOTE=Medah]Do you know what nic is onboard? I have an Abit KV8-MAX3 with 3com 59x card, using the sk98lin driver. I usually have to modprobe this driver manually, altough i cant remember if i did on ubuntu.[/QUOTE]

The onboard nic uses the velocity module which is sadly broken in the kernel version Ubuntu ships.

---

### Post by asparagino on 2004-11-15
Actually, this is fixed as of 18th October.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=1873](https://bugzilla.ubuntu.com/show_bug.cgi?id=1873)

I filed a bug and verified that it now works  \\:D/

---

### Post by latrine on 2004-11-16
thxs... as there was no phisical description of what happened I never Knew the bug was related to velocity... I have updated bug 3018 as to be a copy of yours....

have fun!

---

### Post by davvo on 2004-12-09
I know you solved this already, but in case someone else is having problem with the onboard nic this is how I did it without installing another (pci) network card.

1) Add via-velocity to /etc/modules
2) Add these lines to /etc/network/interfaces:

iface eth0 inet dhcp
name Ethernet LAN card
auto eth0

This should get the onboard nic online (if you are using dhcp).

---

### Post by Silwenae on 2004-12-10
[QUOTE=davvo]I know you solved this already, but in case someone else is having problem with the onboard nic this is how I did it without installing another (pci) network card.

1) Add via-velocity to /etc/modules
2) Add these lines to /etc/network/interfaces:

iface eth0 inet dhcp
name Ethernet LAN card
auto eth0

This should get the onboard nic online (if you are using dhcp).[/QUOTE]
 Thanks for the tips, I just ordered this board yesterday.  Glad I saw this thread!

---

### Post by alionuwka7887 on 2007-05-15
> **Silwenae said:**
> Thanks for the tips, I just ordered this board yesterday.  Glad I saw this thread!


[magnets Yahoo Eminem Cash Advance Eminem](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

