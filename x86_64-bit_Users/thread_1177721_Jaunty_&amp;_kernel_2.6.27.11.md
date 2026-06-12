---
title: "Jaunty &amp; kernel 2.6.27.11"
date: 2009-06-03
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2009-06-03
Hi

I am running Jaunty on running kernel 2.6.27.11. Shouldn't Jaunty kernel be higher...2.6.28.11 or something??


uname -a gives: 
Linux htpc 2.6.27-11-generic #1 SMP Wed Apr 1 20:53:41 UTC 2009 x86_64 GNU/Linux


Cheerz

Bloemetjesgordijn

---

### Post by istblacken on 2009-06-04
uname -a output
2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:31:32 UTC 2009 x86_64 GNU/Linux
I have backports and proposed enabled. Maybe it is related with that..

---

### Post by Yellow Pasque on 2009-06-04
Yes, Jaunty should use 2.6.28 series. Did you upgrade from Intrepid? Maybe you have both the Jaunty and Intrepid kernels installed, and kept your existing /boot/grub/menu.lst file? Possibly useful commands:
```
sudo apt-get dist-upgrade
sudo update-grub
```

---

### Post by Bloemetjesgordijn on 2009-06-11
well 

sudo apt-get dist-upgrade
sudo update-grub

did not work....


So I did myself a clean install of Jaunty...

Now uname -r gives: 2.6.28.11


Bit messy to solve but it works:D

Thx

Kind regards

Bloemetjesgordijn

---

