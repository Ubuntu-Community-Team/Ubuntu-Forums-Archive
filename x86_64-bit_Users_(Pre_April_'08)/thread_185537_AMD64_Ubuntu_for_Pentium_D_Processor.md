---
title: "AMD64 Ubuntu for Pentium D Processor"
date: 2006-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by pkunal on 2006-05-31
I am going to build a PC from scratch using Intel Pentium D 930 (3GHz) and a compatible Intel Motherboard D945GTPLR.

The plan is to have it as an Entertainment/Media PC. I have decided to install Ubuntu Desktop Linux on it.

Please let me know which version of Ubuntu should I install:
Intel x86
AMD64

I have always stayed away from Linux as I am not an expert and installation has been very tough always. Please help me make my life easy.

I really wish to start in the right direction with the correct version installed.

---

### Post by RAOF on 2006-05-31
Easy would be "Intel x86".  There are (slightly) fewer hassles.

---

### Post by Rob2687 on 2006-06-01
Yeah...go with Intel x86. 
64-bit won't provide you with any incredible speed boost or anything and things will be easier for you with x86.

---

### Post by swamytk on 2006-06-01
Yes, go for x86 Ubuntu. Reasons:
1. Many people face driver problems and some odd application issues.
2. You won't feel noticeable performance boost with 64 bit kernel, since most of the applications are 32 bit.

btw: I too analyze hardware configuration a lot to go for a new PC. I came to know that AMD is good for Entertainment/Media/Game related applications. But it is bit costly in some countries like India (in my case). Why can't you consider that?

---

### Post by RAOF on 2006-06-01
[QUOTE=swamytk]Yes, go for x86 Ubuntu. Reasons:
1. Many people face driver problems and some odd application issues.
2. You won't feel noticeable performance boost with 64 bit kernel, since most of the applications are 32 bit.
...[/QUOTE]
I'm not aware of driver problems, apart from getting Windows drivers to work with ndiswrapper.

The second part of this is wrong, at least about the 32bit applications.  If you install the 64bit version of Ubuntu, everything you get from the repositories will be 64bit.

You (generally) won't feel a performance boost, mostly because modern CPUs are so vastly overpowered for desktop use that a difference in CPU power barely affects desktop timing.  You **can** get useful improvements in speed with x86_64, but only if you're doing something that taxes the CPU in the first place - A/V encoding, scientific stuff, etc.

---

### Post by balleklorin on 2006-06-01
I've had no driver problems at all using the 64bit AMD version, no weird application issues either. As metioned above  repositories are 64 bit so I really can't see the big problem. 

I think it's time to jump on the 64bit bandwagon.

---

### Post by pkunal on 2006-06-01
Thanks for the reply.

Important Question:

I did read somewhere that if I install x86 version only one core gets activated. IS THAT TRUE?

Also there is a way to activate both cores through a utility but that is for AMD. HOW TO ACTIVATE BOTH CORES IN Pentium D?

Currently I am inclined to install AMD64, since I am not planning to mess with this stuff very often. Once it starts working thats how its going to be for the rest of the life.

Installing and Uninstalling Linux is a big hassle which I wish to avoid. SO IF AMD64 version does work with Pentium D, then I would rather take the effort once than do it again sometime in the future.

Also some of the other Hardware I have bought is:

1. D-Link Wireless Adapter DWL-510 (seems to work with ndiswrapper & RealTek 8180L Driver with some modifications)
2. Seagate Barracuda 160GB HD 7200.9 (something like that)

Please provide suggestion for an easy-to-install Video Card. I really need the TV Out since I plan to hook it up to the TV. Board has some High-End integrated video.

I hope the kind of DDR2 & HD I have is not going to cause any problems?

I am already losing sleep over the installation process...the parts are not even shipped so far.

---

### Post by JoWilly on 2006-06-01
[QUOTE=pkunal]
I did read somewhere that if I install x86 version only one core gets activated. IS THAT TRUE?[/QUOTE]

No it is not true. Both cores work. Yes, amd64 is what you want for Pentium D.

---

### Post by sheenaramone on 2006-06-01
I just built a Pentium D 920 on an Asus p5ld2-vm motherboard.  I used the 64 bit Dapper 6.06 beta 2 and both cores were detected.  Since I have integrated graphics, I can't really help with the video card selection, but I have always stuck with NVidia cards and they've been fine with Ubuntu for me.

---

### Post by JoWilly on 2006-06-01
And actually, for a pentium D the amd64-xeon kernel would be the best as it is optimized for intel's EM64T.

---

### Post by RAOF on 2006-06-01
[QUOTE=pkunal]Thanks for the reply.

Important Question:

I did read somewhere that if I install x86 version only one core gets activated. IS THAT TRUE?
[/quote]
No.  The default kernel is not SMP (which is what you need for both cores to work), but you can get the linux-686 package, which will get both cores working.

[QUOTE=pkunal]
1. D-Link Wireless Adapter DWL-510 (seems to work with ndiswrapper & RealTek 8180L Driver with some modifications)
2. Seagate Barracuda 160GB HD 7200.9 (something like that)
[/quote]
The harddrive will be no problem, but I don't think that ndiswrapper works **at all** with the AMD64 version (32bit drivers, 64bit kernel, it's just not gonna work).  If your wireless won't work without ndiswrapper, and you must have it, **don't** install the AMD64 version.

---

### Post by pkunal on 2006-06-02
[QUOTE=RAOF]
The harddrive will be no problem, but I don't think that ndiswrapper works **at all** with the AMD64 version (32bit drivers, 64bit kernel, it's just not gonna work).  If your wireless won't work without ndiswrapper, and you must have it, **don't** install the AMD64 version.[/QUOTE]

OK there is a 64 bit Windows Driver available for RealTek 8180L (DWL-510) from RealTek's website. It looks better than 32 bit drivers and I guess it takes out the requirement to update the respective INF file as mentioned in different forums to make it work with DWL-510 (D-Link). I also did read somewhere about ndiswrapper working with AMD64...will have to re-search on that.

I spent time on May 31, 2006 to download AMD64 Ubuntu 5.10.......the very next day I see Ubuntu 6.01...have downloaded that and I hope everything is fine. Life's like that.

By the way someone gave me Xandros 3.0 Desktop Version CD for FREE....but I plan to stick with Ubuntu...any recommedations?

---

### Post by pkunal on 2006-06-02
Other simple question:

When I install AMD64 Ubuntu will ndiswrapper be pre-installed or will I have to install it manually again?

There is a STABLE 1.16 Version, is it included in Ubuntu 6.01 or some previous version?

Thanks.

---

