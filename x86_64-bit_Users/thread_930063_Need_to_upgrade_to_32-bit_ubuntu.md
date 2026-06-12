---
title: "Need to upgrade to 32-bit ubuntu"
date: 2008-09-25
forum: x86 64-bit Users
---

### Post by desdenova on 2008-09-25
Hi,

I have been running Ubuntu Hardy LTS edition for some time now, but I just realised that my kernel is the i686 one... so I wish to upgrade to the 64-bit edition (without losing all the additional softwares I have installed on the current version)

Is this possible... if so, how ?

Thanks for any responses ...

---

### Post by Thelasko on 2008-09-25
[This question is asked about once a week. Please search the forums before posting.]("http://ubuntuforums.org/showthread.php?t=366707")

---

### Post by cariboo on 2008-09-25
The only way you can do an upgrade from a 32bit version to a 64bit version is to do a clean install. Unfortunately th 64bit version will not work with your processor.

Jim

---

### Post by cjazz on 2008-09-26
> **cariboo907 said:**
> The only way you can do an upgrade from a 32bit version to a 64bit version is to do a clean install. Unfortunately th 64bit version will not work with your processor.

Jim

Excuse me? Where does OP identify his or her processor?

---

### Post by Sef on 2008-09-26
> Excuse me? Where does OP identify his or her processor?

From the i686 kernel, if I am correct.  

desdenova: 

If you want to double check if you can use the 64-bit or not:

Applications > Accessories > Terminal

paste or type in this code:

```
uname -m
```

If you can run 64-bit, it will say x86_64.

---

### Post by John.Michael.Kane on 2008-09-26
> **desdenova said:**
> Hi,

I have been running Ubuntu Hardy LTS edition for some time now, but I just realised that my kernel is the i686 one... so I wish to upgrade to the 64-bit edition (without losing all the additional softwares I have installed on the current version)

Is this possible... if so, how ?

Thanks for any responses ...

Without knowing your hardware config, it will be hard for forum members to tell you if you can or cannot run a 64 bit OS.

First to make sure your hardware supports 64 bit you can run the command below. Which will tell you if have a 64 bit aware processor.

```
cat /proc/cpuinfo
```

Regarding your main question of upgrading to 64 from 32 bit. There have been discussions on this and the consensus seems lean to having to do a reinstall, and backing up your data before doing so.

---

### Post by Sef on 2008-09-26
> Regarding your main question of upgrading to 64 from 32 bit. There have been discussions on this and the consensus seems lean to having to do a reinstall, and backing up your data before doing so.

I know of no other way to upgrade to a 64-bit from a 32-bit system.

---

### Post by rsambuca on 2008-09-26
Sef, those instructions you gave don't give the 64 bit info capabilities of the processor.

---

### Post by Sef on 2008-09-26
> Sef, those instructions you gave don't give the 64 bit info capabilities of the processor.


I realized that when I read john's post.  I had thought about cpuinfo, but forgot the differences between that and free -m.

---

### Post by desdenova on 2008-09-30
Hi Again.... 

Thank you all for taking a such a keen interest in this post... and sorry for repeating an oft asked question.

Sef : I am pretty sure my AMD64 processor can  handle a 64-bit OS ;) also - I have already done a cpuinfo to make sure.

Also - I had already checked the earlier posts regarding the same problem with earlier versions of Ubuntu, but was somewhat hopeful... that the latest release would have somehow implemented this feature (although I am not sure of the technical difficulties involved)

As far as I can think, since a 64-bit linux can also run many 32-bit softwares... it should really be possible to enable a person to switch his kernel to a 64-bit one, and still retain his working 32-bit softwares. I do hope this small insignificant features will find its way into Ubuntu in a future release. 

I need to do a lot of setup now... **thanks to you all!!**

**Cheerios!!**

---

### Post by peakshysteria on 2008-09-30
Most 32-bit softwares have 64 bit equivalents. Which is some of the point of changing to a 64 bit OS. No point in running a 64 bit Ubuntu with everything else 32-bit.

---

### Post by desdenova on 2008-09-30
> **peakshysteria said:**
> Most 32-bit softwares have 64 bit equivalents. Which is some of the point of changing to a 64 bit OS. No point in running a 64 bit Ubuntu with everything else 32-bit.

Thanks Peakshysteria... I appreciate your words of encouragement... will surely upgrade my Os -and all the software that i can.

---

### Post by crjackson on 2008-09-30
> **desdenova said:**
> 
As far as I can think, since a 64-bit linux can also run many 32-bit softwares... it should really be possible to enable a person to switch his kernel to a 64-bit one, and still retain his working 32-bit softwares. I do hope this small insignificant features will find its way into Ubuntu in a future release. 

I need to do a lot of setup now... **thanks to you all!!**

**Cheerios!!**

Actually it is possible, just not practicle I suppose. I have never done this myself, but I have read a few posts where the 64-bit kernel was transplanted into a 32-bit install to gain access to large amounts of memory. Upgrading and/or changing all the other libs and packages however would be a different story. I sure it's POSSIBLE but hardly worth the effort.

---

### Post by Thelasko on 2008-10-01
> **crjackson said:**
> ...but I have read a few posts where the 64-bit kernel was transplanted into a 32-bit install to gain access to large amounts of memory.
Wouldn't it be much easier to simply install [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extensions") support?

---

### Post by Sef on 2008-10-01
I would also think about dual booting.   [OpenJDK]("http://ubuntuforums.org/showthread.php?t=774956") is not 100% compatible with Java.  Over 90% of the time it is, but there are sites where it will not work.  It really depends on if your sites are compatible or not with OpenJDK.

---

### Post by crjackson on 2008-10-01
> **Thelasko said:**
> Wouldn't it be much easier to simply install [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extensions") support?

I not arguing the merits, I'm just stating it has reportedly been done.

---

### Post by crjackson on 2008-10-01
oops! double post... sorry.

---

