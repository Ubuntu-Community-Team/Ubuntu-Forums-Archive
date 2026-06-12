---
title: "Core 2 vs Athlon X2"
date: 2006-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mau on 2006-11-18
Hey guys,
I heard that there are problems with the AM2 socket in Ubuntu? I've also heard that Core 2 support is bad in Ubuntu?  Are both of these true?

My next computer will be dual core and 64bit, but I want to know if Ubuntu supports these?  How does Ubuntu compare to other OSes, like Fedora?

---

### Post by Ryan H on 2006-11-18
I don't belive there are any hardware problems with them. Linux supports a wide range of processors, and I know it supports those two. As for the 64-bit version of Ubuntu, the software has it's own problems. But you can always use the 32-bit version.

-Ryan H

---

### Post by The Warlock on 2006-11-18
> **Mau said:**
> Hey guys,
I heard that there are problems with the AM2 socket in Ubuntu? I've also heard that Core 2 support is bad in Ubuntu?  Are both of these true?

My next computer will be dual core and 64bit, but I want to know if Ubuntu supports these?  How does Ubuntu compare to other OSes, like Fedora?

As far as I know there aren't any problems with either, aside from the problems that every 64-bit processor has if you're running the 64-bit version (i.e. no Flash, etc). Run the 32 bit version if you really need Flash or whatever or run the 64 bit version if you've crammed an obscene amount of RAM in the box.

I believe SMP support is built into all of Ubuntu's kernels by default now (although it wasn't always like that) so no worries there, either.

---

### Post by Mau on 2006-11-18
Thanks guys.  Is there anything that I should look for that won't work?

In particular, will nForce 5 work?

---

### Post by kuja on 2006-11-19
I've heard of some problems related to the Core 2 and AM2 motherboards. Big problems, I'm not sure what the status on that is right now.

---

### Post by foxmulder881 on 2006-11-19
Sound like a lot of rumors and not much fact. People are saying these are reoprts of problems yet nobody actually seems to know what problems exactly.

---

### Post by Lonthong on 2006-11-19
Posting this from BenQ P41 laptop (Turion X2 + ATI Xpress 1100).
No problem running 64bit Dapper Drake so far........
Also installation was very smooth

---

### Post by cidian on 2006-11-19
i am running a core 2 duo and ubuntu 64bit and it works great

---

### Post by carlgm on 2006-11-19
I would suggest going with Intel Core Duo 2 over AMD X2.

---

### Post by Azakus on 2006-11-19
I'm running on an Athlon X2 right now with no problems whatsoever related to the processor. That Beryl crashes every once and a while doesn't count. For flash and other 32-bit only browser plugins. Install Swiftfox and Automatix2. Swiftfox is the 32-bit optimized build of Firefox for each processor and runs perfectly in 64-bit Linux. Automatix has the 32-bit plugins for Swiftfox, so just install those and you'll be good to go.

---

### Post by RAOF on 2006-11-19
> **foxmulder881 said:**
> Sound like a lot of rumors and not much fact. People are saying these are reoprts of problems yet nobody actually seems to know what problems exactly.

Specifically, there were problems with the IDE controller on some of the new Core2 motherboards being not supported.  At all.  So people just couldn't install.

I think that got fixed in the Edgy kernel, though.  The (jmicron2, IIRC) driver got merged in.

---

### Post by BILAN on 2006-11-20
Hmmm..  Have anyone actually gotten ver 6.10 to work on the Athlon 64 dual core?  I am trying to boot it up from a CD image, but it hangs during the splash screen.  The only possible problems I can see is either a processor incompatibility or my graphics card (an old Voodoo3).  I doubt if it's the graphics card since it hung even when booting in safe graphics mode.

I would like to know if what version, if any, anybody has successfully booted with the AMD64 X2.  Thanks.

---

### Post by oxman on 2006-11-20
I am using a opteron (175) dual core 64, asus a8n-sli deluxe mobo with dapper without a hitch. I have used both the generic and the k8 kernal wihtout a problem.

---

### Post by solarwind on 2006-11-20
Lol, good question, but no. They wont have any outstanding problems like windows. Linux pwns smp. And go for amd athlon x2. Intel wont stay ahead for long with their core2duo. AMD was, is and always will be better than intel. AMD is coming out with something that'll blow intel out of the water.

:twisted: :twisted: :twisted: :twisted: :twisted: :twisted: :twisted: :twisted:

---

### Post by RAOF on 2006-11-20
> **solarwind said:**
> Lol, good question, but no. They wont have any outstanding problems like windows. Linux pwns smp. And go for amd athlon x2. Intel wont stay ahead for long with their core2duo. AMD was, is and always will be better than intel. AMD is coming out with something that'll blow intel out of the water.


Except, of course, for that whole period before the K7 came out where they just had poor-man's versions of intel chips.  It was only with the Athlon (k7) and particularly the Athlon64 (k8) that they really began competing with Intel chips on speed.  Currently, the new Intel Core 2 chips are better (faster and less power-hungry) than the Athlon X2s.  That will probably change again, as it has in the past as AMD and Intel have released new chips, but I just don't see how anyone could say "AMD was, is and always will be better than intel".  You're buying a CPU, not a religion.

---

### Post by jcaveman on 2006-11-21
If your having trouble booting the AMD X2, try using the noapic kernel options.  It worked for me.

---

### Post by Cynical on 2006-11-22
You should buy AMD because they support linux much better than Intel does. They should be coming out with their newer processors soon to challenge Intel's core 2 line. I have a core 2 myself and the big problem that we faced with Intel deciding not to include ide support in their chipset (where are the cheap sata drives eh?) was solved as edgy was being released. I'm definitely going AMD next time around. (cant wait for fusion)

---

### Post by pharcyde on 2006-11-23
Both are a good choice.  If you want the latest and greatest go with Intel.  If you are looking to the future then there is no telling who will be on top.  Currently Intel is king of the desktop. It will probably change to AMD in teh near future and bounce back and forth like the NVIDIA/ATI gpu products.  The good news is both are compatible x86-64 ISA so there shouldn't be a problem with either chipset in linux.

---

### Post by finite9 on 2006-11-23
agree with pharcyde...it's all swings and roundabouts (or whatever they are called in the US...circulations?).

*At the moment* Core2Duo is the technically superior product.  As long as you're not a principals fanatic, then this is currently the chip to buy...less power hungry and faster than AMD Turion X2.  If you are concerned about Intels lack of support to the Free software community, and value that above technical superiority, then get an AMD.

I personally value free software and I would not buy a peripheral (now) that has no supported driver for GNU/Linux, but I draw the line at processors, where there is no driver involved and both work equally well with the right kernel.  I wouldn't get hung up about how much they support the community in other ways.

---

### Post by jUser on 2006-11-23
> **foxmulder881 said:**
> Sound like a lot of rumors and not much fact. People are saying these are reoprts of problems yet nobody actually seems to know what problems exactly.

Take a look at [https://wiki.ubuntu.com/Core_2_Duo_Support]("https://wiki.ubuntu.com/Core_2_Duo_Support").

I think any AMD 64-bit processor seems to be a good choice for Linux. Intel may have the fastest processors at the moment, but if you look at the performance/price ratio, AMD might win.

This is posted from a AMD Turion-based laptop, working great with the x86_64 versions of both Ubuntu 6.10 (Edgy) and Fedora Core 6.

---

### Post by daradib on 2006-11-23
> **BILAN said:**
> I would like to know if what version, if any, anybody has successfully booted with the AMD64 X2.  Thanks.

I have used Kubuntu 6.10 64-bit with AMD Athlon64 4400+. No problems save for a graphics card problem which is unrelated.

> **BILAN said:**
> but it hangs during the splash screen

I had the same problem (even with Kubuntu Edgy 32-bit), but that has to do with my ATI Radeon X800 card and drivers. Safe graphics mode does not help. The drivers that come with Ubuntu/Kubuntu must be replaced. I use the fglrx drivers instead (they are proprietary and closed source). I had to do Ctrl-Alt-F1 to stop kdm (correct me if I'm wrong) and then installled fglrx drivers via apt in console and configured.

---

