---
title: "ati proprietary driver for kerel 2.6.25"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by Joker5bb on 2008-06-26
Hi there guys i need some help installing the ati proprietary driver for Ubuntu Hardy. I have a custom compiled kernel 2.6.25.6. I have tried to install it but i get a black screen when i restart the comp after enabling it from the restrictive hardware panel.

i have download the linux ati driver from
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

then i ran   
sudo sh ati-driver-installer-8-6-x86.x86_64.run

and the installation went fine but do i have to add patches or make extra configuration?

:lolflag:

---

### Post by Joker5bb on 2008-06-26
o i got to work just follow the directions here:

[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

---

### Post by 50below on 2008-07-02
mine just dont wanna work...am stuck in "safe" graphics mode -.- lovely and cant seem to shift it now...followed the instructions...STUCK WITH DAMN MESA drivers :'( :confused: ](*,)

i've offically given up ima swap my mobos around and use my AGP board with my lovely Gforce FX5200 (ima have more luck with this than damn ATI) any want an X1650?

---

### Post by MaindotC on 2008-07-11
50 I feel your pain.  I posted a couple times w/ the same issue.  All I wanted to do was go back from the ATI driver I downloaded to the one that was in the repos.  I tried a lot of things and still got Vesa and everytime I changed it and restarted X it would go right back to Vesa.

This is the tweet I just posted:

"ALMOST **** MY PANTS - changed xorg.conf, restarted X and got the dreaded "log-graphics mode". Thankfully I replaced xorg.conf w/ a backup!"

---

### Post by bpl07 on 2008-07-11
> **strAlan said:**
> 50 I feel your pain.  I posted a couple times w/ the same issue.  All I wanted to do was go back from the ATI driver I downloaded to the one that was in the repos.  I tried a lot of things and still got Vesa and everytime I changed it and restarted X it would go right back to Vesa.

This is the tweet I just posted:

"ALMOST **** MY PANTS - changed xorg.conf, restarted X and got the dreaded "log-graphics mode". Thankfully I replaced xorg.conf w/ a backup!"

The driver in the repos is catalyst 8.1, which does not support kernel 2.6.25.  You have to use the most recent driver (catalyst 8.6), which is the first driver with support for kernel 2.6.25.  FYI, there is still no proprietary ati driver with support for kernel 2.6.26.

---

### Post by Joker5bb on 2008-07-11
yes thanks for that info,because i have compiled 2.6.26-rc9
and was having trouble. here is the error:

have build these packages. from ati-driver-installer-8-6-x86.x86_64.run

joker@joker-laptop:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
(Reading database ... 222943 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 2:8.501-0ubuntu1 (using xorg-driver-fglrx_8.501-0ubuntu1_amd64.deb) ...
 * Stopping atieventsd                                                   [ OK ]
Unpacking replacement xorg-driver-fglrx ...
Preparing to replace fglrx-kernel-source 2:8.501-0ubuntu1 (using fglrx-kernel-source_8.501-0ubuntu1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Preparing to replace fglrx-amdcccle 2:8.501-0ubuntu1 (using fglrx-amdcccle_8.501-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Setting up xorg-driver-fglrx (2:8.501-0ubuntu1) ...
 * Starting atieventsd                                                   [ OK ]

Setting up fglrx-kernel-source (2:8.501-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.26-rc9-wl (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.501/build/ for more information.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.26-rc9-wl (x86_64) first.
Done.

Setting up fglrx-amdcccle (2:8.501-0ubuntu1) ...

---

### Post by Joker5bb on 2008-07-11
guys read this 

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/2:8.501-0ubuntu4](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/2:8.501-0ubuntu4)

and install the deb packages!

---

### Post by Joker5bb on 2008-07-11
so yes i got my ati card working in 2.6.26-rc9
and correction catalyst 8.5 works in 2.6.26, 
8.6 is not yet supported with amd 64
:lolflag: :lolflag: :lolflag: :lolflag: :lolflag: :lolflag:

---

### Post by bpl07 on 2008-07-12
I think fglrx 8.501 is catalyst 8.6.

---

