---
title: "AMD Sempron 3300+: Which ISO must I download (i386/amd64)?"
date: 2009-01-10
forum: x86 64-bit Users
---

### Post by guarriman on 2009-01-10
Hi.

I've got an "AMD Sempron 3300+" PC where I want to install Ubuntu 8.10:

Browsing this download webpage
[http://ftp.stw-bonn.de/ubuntu-cd/intrepid/](http://ftp.stw-bonn.de/ubuntu-cd/intrepid/)
I find two different ISO files:
1) ubuntu-8.10-desktop-amd64.iso
2) ubuntu-8.10-desktop-i386.iso

Which one is for me? Thank you very much.

---

### Post by paddy2706 on 2009-01-10
please use ubuntu-8.10-desktop-i386.iso for your cpu, which does not have 64-bit support.

---

### Post by phlembob on 2009-01-10
Hi,
Your Sempron does have 64 bit capability.  I believe it will be your choice of which way to go.  Semprons are energy savers a short time ago and were used in many laptops.  Of course they were used in desktops also.

Your choice!  Good Luck
:guitar:

---

### Post by Yellow Pasque on 2009-01-11
Some Sempron 3300's did not have 64-bit support. Make sure your CPU supports 64-bit before you waste a CD downloading the amd64 version.

If you're currently running another Linux/LiveCD, use:
```
cat /proc/cpuinfo
```
If you see "lm" (long mode) listed under the flags, your CPU is 64-bit capable.

If you're running Windows, there are freeware programs that give you info on your CPU.

---

### Post by phlembob on 2009-01-11
Your Sempron is a 3300(+).  It was available in sockets 754 and AM2.  It was AMD equivalent to Celeron.  It was better than Celeron and it gave Pentium performance with low power consumption.  It made laptops go for 2 hours without a charge.  That was a feat --- if you remember the days when laptop batteries were exploding, chuckle.  They have changed the battery composition but it was a 200 million dollar blow to the Sony Corp.  I would imagine that it was closer to .5 billion after their workforce physically swapped batteries and the shipping charges to change out those batteries.

Anyway, your 3300+ Sempron is 64 bit compatible.  It is your choice.

:guitar::lolflag:

---

### Post by Yellow Pasque on 2009-01-11
> Anyway, your 3300+ Sempron is 64 bit compatible.
Not necessarily. SOME Socket754 3300's did not have 64-bit. (Look it up on AMD's site if you don't believe me.)

---

### Post by phlembob on 2009-01-11
I went through the News releases and FAQs.  Temujin could have a point because none were conclusive, but one release did say 64 bit technology is "now" available in 3300+ (and lower numbers) for full size notebooks/laptops.  4000+ was the only conclusive release as it was written.

Ok, I guess there were i386 models with the same number with the + (and) sign.  Thanks Temujin for showing the unclearity in AMD script.  It isn't clear even now.

The judgment is still yours because it did note "Full size" which is my reference for 15.4 " and above notebook size styles.  And because that was noted I would "assume" that would be the most likely used in a desktop also because of the 95nm technology.  65 and 55 nm was not available when 3300+ were released.

Ask yourself - is my laptop a full size?  Desktop?  It still comes down to guess work.  ):P

---

### Post by felker2 on 2009-01-11
> **guarriman said:**
> Hi.

I've got an "AMD Sempron 3300+" PC where I want to install Ubuntu 8.10:

Browsing this download webpage
[http://ftp.stw-bonn.de/ubuntu-cd/intrepid/](http://ftp.stw-bonn.de/ubuntu-cd/intrepid/)
I find two different ISO files:
1) ubuntu-8.10-desktop-amd64.iso
2) ubuntu-8.10-desktop-i386.iso

Which one is for me? Thank you very much.

The i386 is always OK so it's always safe to use that ISO.

If you want to go 64 bit (which can be useful if you have more than 3GB RAM or if you want to experience 64-bit), you first have to check whether your Sempron 3300 is 64-bit. Running Linux (installed, or from live CD), check the output from 

```
grep --color lm /proc/cpuinfo

```
If it gives any output (with "lm" in color), you have a 64-bit CPU, and you can run AMD64.

HTH

---

