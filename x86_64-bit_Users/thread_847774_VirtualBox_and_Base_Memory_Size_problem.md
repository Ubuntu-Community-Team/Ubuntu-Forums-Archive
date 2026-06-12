---
title: "VirtualBox and Base Memory Size problem"
date: 2008-07-02
forum: x86 64-bit Users
---

### Post by kimolias on 2008-07-02
After failing to install VirtualBox from synaptic I downloaded 1.6.2 from the official website.

Versions:
VirtualBox 1.6.2 (NOT the OSE one)
with guest additions installed and USB support
Ubuntu 8.04 (hardy)
Gnome 2.22.2
Kernel 2.6.24-19-generic

After successfully installing Windows XP (SP3, also tried SP2 and had the same behavior) with the default Base Memory Size I then decided to "add more memory". At first I set it to the maximum (2GB). When Windows booted, it started to have a lot of hard disk activity. Actually, it had so much, that my system hanged and I couldn't do anything other than reseting it. At first, I thought the 2GB was a wrong choice so I then set it at 1024MB, which was a little better, but again, my system hanged due to high hard disk activity. Fortunately, this time I could barely "Force Quit" VirtualBox and the system came back up.

Note that, when I say hard disk activity, I'm mentioning the LED that is constantly being lit when this happens, as opposed to rarely doing this on normal system loads.

I can assure you that this is probably an Ubuntu problem since a month ago I used VirtualBox normally in openSuSE 10.3 with more than 1024MB of Base Memory Size. On the other hand, I just bought a new hard disk SATAII but I kinda doubt this is the problem.

Any suggestions on fixing this?

Thank you in advance.
Panagiotis

---

### Post by incubii on 2008-07-03
It seems like your machines is swapping out a lot due to the VM using 1gb+ of RAM all i can suggest is say setting ti to 512mb or even 256mb and see if your HDD goes crazy still. Least then you know its RAM

---

