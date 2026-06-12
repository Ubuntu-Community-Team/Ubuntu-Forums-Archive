---
title: "ubuntu on Quad-Core Intel systems?"
date: 2008-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by penguy on 2008-01-10
Hi,

I am currently running Vista Ultimate/64 on my HP quad-core Intel system and I realize that this forum is for AMD-based systems, but wanted to find out if ubuntu runs on a system configured such as mine?

I'm sick of Vista after 3 months and it's constant updates and security fixes and want to try ubuntu.


Thanks in advance.

---

### Post by ~LoKe on 2008-01-10
I've used 32bit Ubuntu on my Q6600, and am currently running the 64bit release without issues.

---

### Post by impact on 2008-01-10
AMD based? What do you mean by that. Intel makes 64-bit processors, too.

I think the easiest way to see if it works would be to try a 64-bit live CD:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by saru411 on 2008-01-10
amd64 is the architecture of the chip, not the brand. amd named their company after the architecture that they developed i believe.

---

### Post by ~LoKe on 2008-01-10
> **impact said:**
> AMD based? What do you mean by that. Intel makes 64-bit processors, too.

This "section" of the forums is based around AMD64, which was developed by AMD.  But 64bit Intel and AMD processors both work just as well.

---

### Post by crjackson on 2008-01-10
> **saru411 said:**
> amd64 is the architecture of the chip, not the brand. amd named their company after the architecture that they developed i believe.

No they didn't.  AMD has been around since at least 8/16 bit processors/chipsets.  The amd64 distro works on both amd/intel.

---

### Post by ~LoKe on 2008-01-10
> **crjackson said:**
> No they didn't.  AMD has been around since at least 8/16 bit processors/chipsets.  The amd64 distro works on both amd/intel.

Uh...
> x86-64 is a 64-bit superset of the x86 instruction set architecture. The x86-64 instruction set natively supports Intel's x86 and was designed by Advanced Micro Devices (AMD), who have since renamed it AMD64.
AMD designed the x86-64 superset, and thus named it after themselves, making it AMD64.

---

### Post by crjackson on 2008-01-11
> **~LoKe said:**
> Uh...

AMD designed the x86-64 superset, and thus named it after themselves, making it AMD64.

No one said anything to the contrary.  It seems you didn't read closely the post I replied to.  AMD did NOT name it's company after the architecture.  The architecture was named after the company.

I had amd (Advanced Micro Devices) chips YEARS before there was an AMD64.

---

### Post by Cenotaph on 2008-01-11
AMD64 and Intel 64 both implement the same superset to some extent and programs are usually compiled to use the common features between the 2 so they are compatible with both architectures, although there are some differences between AMD64 and EM64T, they are essencially identical, and are pretty much treated as the same for commercial reasons.

64-bit processors from AMD and Intel (not IA-64, but Intel 64) are supported by this AMD64 version of Ubuntu. This forum is not specially dedicated to one of them.

---

### Post by jrusso2 on 2008-01-11
Maybe its time to rename those iso's
 as it is confusing to some.  When they see AMD64 they think its only for AMD cpus?

---

### Post by jrickard on 2008-01-12
Maybe so.  But it does point up a clue here.  I have an AMD dual opteron with a fairly recent NVIDIA card and haven't had a single lockup.

I also have a newer Intel QX6850 with the NVIDIA 8800 Ultra.  I have tried everything in the freezups thread, but it still locks up every 2-4 hours and has since I installed Gutsy.  Runs Vista without problems.  

There is definitely a Ubuntu problem with the Intel Quad architectures and it seems to have something to do with the NVIDIA drivers.  But nobody seems to be able to pin it down.  Worse, it may very well be a kernel problem.  I keep thinking there will just be a quiet software update at some point and the lockups will disappear.  But it has been months already.

Jack Rickard

---

### Post by mavicus on 2008-01-12
I have been running 64 bit 7.04 and 7.10 Ubuntu since their releases on an Intel Quad-Core processor and 8GB ram, and have never had any kind of freezups whatsoever except for a few minor software hangups that I believe are related to hard drive issues only. Never rebooted because of freezups, only because of glitches with sound or because of updates.

Using:
Asus p5n-e sli motherboard
quad-core processor
geforce 8500GT video card
8GB ram

---

### Post by williammanda on 2008-01-12
I have both Intel core 2 duo 6400 and AMD 64 2x 4200. I did experience some pink screens when using mythtv and xine but I have since installed the lastest nvidia driver 169.07 and have had no problems.
Thanks

---

### Post by Yellow Pasque on 2008-01-12
> **jrusso2 said:**
> Maybe its time to rename those iso's
 as it is confusing to some.  When they see AMD64 they think its only for AMD cpus?
There's no reason to rename the distros. The architecture is called AMD64 and there are lots of software packages and linux distros that have it in the name. Intel did come out with its own version (EMT64) , but it's mostly a copy of AMD's architeture/instruction set.

---

### Post by impact on 2008-01-23
> **jrusso2 said:**
> Maybe its time to rename those iso's
 as it is confusing to some.  When they see AMD64 they think its only for AMD cpus?

Good idea. I know I was confused the first time I searched for the 64-bit version (I have an intel CPU).

---

### Post by saru411 on 2008-01-23
> **crjackson said:**
> No one said anything to the contrary.  It seems you didn't read closely the post I replied to.  AMD did NOT name it's company after the architecture.  The architecture was named after the company.

I had amd (Advanced Micro Devices) chips YEARS before there was an AMD64.

this is what i had meant to say. AMD64 is the architecture of the chip. This architecture was developed by AMD therefor they named the 64 bit architecture AMD64. sorry if i confused anyone.

---

### Post by Peior Crustulum on 2008-01-24
I agree that it might be time to change the naming scheme of the 64-bit ISO's.
There is a profoundly good reason to do so also.

Ubuntu is getting a whole lot of attention these days, and lots of inexperienced computer users decide to give it a shot.
They might not have the in dept knowledge of chipset architecture and naming history that you guys do, but have a fair understanding of the two competing companies that are called AMD and Intel. 
So by having the ISO's named AMD64 might just convince them that it is indeed to be used with AMD CPU's only.

Just because it's not so, does not mean that appearances can't be deceiving.

Agreed?

---

### Post by Jouke74 on 2008-01-24
I think renaming the whole architecture would be a bit drastic as also a lot of non-Ubuntu debian packages will probably not be compatible anymore. Not to mention the number of changes that need to be made to certain programs like Synaptic, DPKG etc.

However, the Dutch translation of the download page of Ubuntu is very sparse with giving information about the processors for which AMD64 is compatible. It states EMT64 and AMD64, but I don't think many Intel buying people know EMT64. They do now Core 2 Duo E6600 etc. Maybe a bit longer explanation on the website will already be sufficient together with some examples of supported processors.

---

### Post by zzHanks on 2008-02-12
> **~LoKe said:**
> I've used 32bit Ubuntu on my Q6600, and am currently running the 64bit release without issues.
I have AMD Athlon 64 dual core. I'm thinking about upgrading to Quad core (to get better software support by running the 32-bit version).
Am I getting this right? (I'm new to ubuntu).

Why did you go to the 64-bit version?

---

### Post by Sunforge on 2008-02-12
> **penguy said:**
> 
I am currently running Vista Ultimate/64 on my HP quad-core Intel system and I realize that this forum is for AMD-based systems, but wanted to find out if ubuntu runs on a system configured such as mine?

U64 Gutsy runs just fine on Intel Quad core, I've run it up on single and dual quad systems and they're perking along. The only disturbing thing that U64 surprises some people with is the lack of splash screen on boot up, which is addressed here:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

If you have more than 3 Gb RAM then 64 bit is definitely worth it. If not - it's a moot point whether you'll see **significant enough** performance gains to make it worth your while.

---

### Post by Yellow Pasque on 2008-02-12
> If you have more than 3 Gb RAM then 64 bit is definitely worth it. If not - it's a moot point whether you'll see **significant enough** performance gains to make it worth your while.
I disagree. The 64-bit version should be used if the hardware supports it, as it does run faster and there's no good reason not to run it.

---

