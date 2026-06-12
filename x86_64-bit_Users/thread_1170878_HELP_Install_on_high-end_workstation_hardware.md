---
title: "HELP: Install on high-end workstation hardware"
date: 2009-05-26
forum: x86 64-bit Users
---

### Post by jps0 on 2009-05-26
I am currently building a high-end workstation for a client who originally spec'ed Win XP 64-bit, but now also wants to dual-boot with Ubuntu or Kubuntu 64-bit as well.   I am a few years removed from regular linux support, so I wanted to see if there would be any "GOTCHAs" I should watch out for with the following hardware:

MOTHERBOARD: Supermicro X8DAi
CPU(s): 2 x Xeon 5540 (2.53GHz)
RAM: 48GB (12 x 4GB) Crucial DDR3 ECC/Registered
VIDEO: Basic nVidia GeForce 9400 GT
RAID Controller: Areca ARC-1680IX-12 (4GB)
BOOT ARRAY: 2 x [Fujitsu MBA3073RC 73.5GB SAS HDDs ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822116057")(RAID 1)
SCRATCH ARRAY: 2 x [Fujitsu MBA3300 MBA3147RC 147GB]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822116058") SAS HDDs (RAID 0)
STORAGE ARRAY: 4 x WD RE3 WD1002FBYS 1TB SATA HDDs (RAID 10)

I am intending to do a basic desktop install of the 64-bit version of Ubuntu or Kubuntu.  is desktop what I should go with or would it be better to go server and then add on the bits I need.  The workstation is a pure number cruncher - it will not be a true 'server'.

Thanks in advance for your help...

---

### Post by pixel :-) on 2009-05-27
I think hardware compatibility between 32bit and 64bit is almost identical
You may prefer re post here
[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

or beter in the server forum
[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

normal users(primarily here) aren't acostumed with this kind of hardware.

You should use the alternative CD. It gives you an option "install command line system".
I never installed the server version, so i have no clue.
The desktop version will do a default install of a million things, you don't want that. I suspect the server version does something similar with server programs, but as you said, its not going to be areal server.

---

### Post by Anubis on 2009-05-27
Dude, install it and tell us how it flies. Seriously, it should install fine.

---

### Post by lisati on 2009-05-27
I wish I had the budget for specs like that! Sigh..... dreams are free.

I think the server edition has a minimal-install option where you don't need to install all the server apps, and a GUI can be added later if you choose.

---

### Post by jps0 on 2009-05-29
For anyone that is curious, Kubuntu 9.04 64-bit installed without one single hitch.  And yes, it screams on that hardware.  Too bad I have to turn it over to my client on Monday - :(

---

