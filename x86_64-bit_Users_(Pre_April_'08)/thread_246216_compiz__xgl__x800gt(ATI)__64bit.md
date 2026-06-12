---
title: "compiz / xgl / x800gt(ATI) / 64bit"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by alexandermimix on 2006-08-28
anyone know of a definitive tutorial for installing this sexy eye candy on my computer? my last attempt broke ubuntu :(

---

### Post by alexandermimix on 2006-09-03
ill take that as a 'no' then ](*,)

---

### Post by loco on 2006-09-09
> **alexandermimix said:**
> anyone know of a definitive tutorial for installing this sexy eye candy on my computer? my last attempt broke ubuntu :(

I have the same problem, x800GT using fglrx driver and amd64 system, I tried to install xgl and compiz from the repos and everithing was ok but i didnt have 3d acceleration on xgl :frown:

If anyone make it with amd64 and ATI please tell us!

---

### Post by AsteriskNix on 2006-09-10
fresh install of 6.0.6.1 amd64 and an ati all in wonder x1900 .


I'll be logging what I do and we'll see about getting some sort of definitive document on this flavor of desktop shall we?

---

### Post by AsteriskNix on 2006-09-10
that's on an opteron 170 btw, not athlon.

---

### Post by fistfullofroses on 2006-09-10
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

---

### Post by togume on 2006-09-10
@ Fistfullofroses, 

What else did you have to do to get compiz working?

Thanks!

Tomas

---

### Post by fistfullofroses on 2006-09-10
I went ahead and installed from source. On the 32bit Ubuntu you can just download from apt and everything you need is there, then you just edit some config files. On 64bit I had no luck with that, and downloaded the source. When you do ./configure when it fails look at what it failed for, if there is a dependancy problem you should be able to use apt-get to get the dependant packages.

---

### Post by togume on 2006-09-17
Good to know.

Would you mind telling me which packages you downloaded? Was it just compiz? Also compiz-manager?

I am going to try to put together a brief tutorial for this, so any more infor would be greatly welcome.

---

### Post by zero gravity on 2006-09-18
Followed the instructions on this site [http://ubuntuforums.org/showthread.php?t=133427](http://ubuntuforums.org/showthread.php?t=133427)
It worked like a charm, hope it helps.

---

### Post by hannav85 on 2006-09-20
Zero Gravity, seeing as you managed to follow the guide, could you tell me how you got the bit below to work? (I went to the server as instructed, saved the four files to my desktop and then put in the code, first without sudo which came up with "dpkg: operation requires read/write access to dpkg status area." With sudo: "dpkg: error processing --force-all (--install):
 cannot access archive: No such file or directory" )



. Install Packages

Now to install the all-important packages.
Credit goes to mikalh for these. I have mirrored them on my own server:

[http://pdc.me.uk/ubuntu/xgl/](http://pdc.me.uk/ubuntu/xgl/)
Download all 4 packages.

To install the packages:
Code:

dpkg --force-all -i compiz_cvs20060218+opacityplugin-1_amd64.deb dpkg --force-all -i glitz-cvs_0.5.3+cvs20060218-1_amd64.deb dpkg --force-all -i mesa-cvs_20060218-1_amd64.deb dpkg --force-all -i xorg-xgl_0.0.1+cvs20060218+patch-1_amd64.deb

*I think it was only the glitz package that needed to be forced but it won't do any harm to do them all.


Im rather confused by this as im still rather new to ubuntu :confused: 

(I am running amd athlon 64 and have 64 bit ubuntu installed)

Thanks in advance, Hanna

---

