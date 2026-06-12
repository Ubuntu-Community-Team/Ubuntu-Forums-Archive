---
title: "Epiphany: closing youtube page crashes X-server"
date: 2007-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by lordmyth on 2007-12-21
I'm having some trouble with flash and epiphany (I don't know if the same problem appears in firefox)
Some times (not always) when I close a tab with a youtube flash video the whole X-server crashes, I've never had this before and it's really annoying :(
Anyone know what the problem could be?

---

### Post by confy on 2007-12-21
interesting... well you can give as more info. Like where from you've download flash (there is not offical flash for 64 machines). When did it start? Is it in every flash site or only youtube?

---

### Post by lordmyth on 2007-12-21
I've used that flash installer script that's popular now, but it happened with the official flash installer from adobe too...

I think it's more than just youtube, at least i seem to remember such a thing - i also think the crashes happen when i'm not viewing the page i'm closing

I'll try to remember the sitiuation more correctly when it happens again

---

### Post by lordmyth on 2007-12-23
correction: it happens on any page containing flash

---

### Post by bigsam72 on 2008-04-02
Hi i observed the same problem with firefox ( version 2.0.0.12 and 2.0.013 and probably all previous versions do that). I think that there is bug somwhere within xserver. sometimes let say after 2-3 days when i am closing tab probably with flash video ( it doesn't matter if it is youtube or something else ) whole xserver crashes. I am using compiz-fusion (from default ubuntu repository + gnome). 


ii  flashplugin-nonfree                        9.0.48.0.2+really0ubuntu12.2         Adobe Flash Player plugin installer

ii  firefox                                    2.0.0.13+1nobinonly-0ubuntu0.7.10    lightweight web browser based on Mozilla
ii  firefox-gnome-support                      2.0.0.13+1nobinonly-0ubuntu0.7.10    Support for Gnome in Mozilla Firefox

ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux nucleus 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64
Build Date: 18 January 2008

HW specs: AMD64 + 2GB RAM
ii  linux-restricted-modules-2.6.22-14-generic 2.6.22.4-14.10                       Non-free Linux 2.6.22 modules on x86/x86_64
Linux nucleus 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 47
model name      : AMD Athlon(tm) 64 Processor 3000+
stepping        : 2
cpu MHz         : 1800.000

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1) (prog-if 00 [VGA])

ii  nvidia-glx-new                             100.14.19+2.6.22.4-14.10             NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu7                    NVIDIA binary kernel module common files

---

### Post by aloshbennett on 2008-05-14
I'm also having this trouble :(.

Has anyone got a solution/lead/hack on this?

---

