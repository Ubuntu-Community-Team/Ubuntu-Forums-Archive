---
title: "i386 or AMD64"
date: 2005-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by ~J~ on 2005-09-07
My processor is an AMD64 San Diego 3700.

Have I "GOT" to use the AMD distro, or can I use the i386 version?  I've read somewhere that for most cases, AMD64 users can (and should) use the i386 version.

---

### Post by heimo on 2005-09-07
No personal experience, but I can say with confidence that you can run 386 version of Ubuntu on AMD Athlon 64 processors (it's backwards compatible). Of course in that case you will be using 32-bit applications.

---

### Post by drummer on 2005-09-07
Yes you can, I have an Athlon64 3000 and use the 386 version of Ubuntu. heimo is right, no issues as 64bit chips are backwards compatable, but you will only be utilising 32bit processing from the chip.

---

### Post by puppy on 2005-09-08
Perhaps also worth pointing out that while the 64-bit version of Ubuntu is great,  there are some quite important apps that are still not available, so for the time being, for instance, you won't be able to see flash animations in your webbrowser, read pdf documents etc. 

Have a look at some of the other threads where people are either writing their own 64-bit versions of these apps and making them available to us poor mortals   :)  or are petitioning the big companies to get their fingers out and release 64-bit versions  ](*,)

---

### Post by rafakl on 2005-09-08
Is it posible to install ubuntu 64 and use 32 bit version repositories????

 O:)

---

### Post by DancingSun on 2005-09-08
[QUOTE=puppy]Perhaps also worth pointing out that while the 64-bit version of Ubuntu is great,  there are some quite important apps that are still not available, so for the time being, for instance, you won't be able to see flash animations in your webbrowser, read pdf documents etc. 

Have a look at some of the other threads where people are either writing their own 64-bit versions of these apps and making them available to us poor mortals   :)  or are petitioning the big companies to get their fingers out and release 64-bit versions  ](*,)[/QUOTE]
You can read pdf documents in Ubuntu 64.  The xpdf program that came with the installation works just fine.

---

### Post by DancingSun on 2005-09-08
[QUOTE=rafakl]Is it posible to install ubuntu 64 and use 32 bit version repositories????

 O:)[/QUOTE]
Search for "32-bit chroot" or "chroot32" in the forums.  There's a "force architecture" option in Synaptic, but I've never used it, so I don't know if it's safe to do so.

---

### Post by mlomker on 2005-09-08
[QUOTE=puppy]instance, you won't be able to see flash animations[/QUOTE]

I couldn't get the version that came with Hoary to work at all--Firefox would close every time.  [This version](http://www.steiner-web.info/rafael/flash/)  works *most* of the time, but the browser will still simply close once in a while.  Give it a try:

---

### Post by slusken on 2005-09-09
I have got an amd 64 3200+ Cpu, I did not manage to install ubuntu 32bit version.
It lags to much during installation. Since it was the first time i installed the ubuntu i had to partition my hdd. It started and i went to bed. The nest morning (8hours later) it was only 45% on its way. Then i tried ubuntu amd64 version. Works almost like a dream. 
Any ideas what i did wrong? I want to run the 32  bit versjon.

And if anyone of you live in Bergen- Norway, I sure could need som help.

Sverre.
_________
Newbie that wants to learn.

---

### Post by drummer on 2005-09-09
[QUOTE=slusken]I have got an amd 64 3200+ Cpu, I did not manage to install ubuntu 32bit version.
It lags to much during installation. Since it was the first time i installed the ubuntu i had to partition my hdd. It started and i went to bed. The nest morning (8hours later) it was only 45% on its way. Then i tried ubuntu amd64 version. Works almost like a dream. 
Any ideas what i did wrong? I want to run the 32  bit versjon.

And if anyone of you live in Bergen- Norway, I sure could need som help.

Sverre.
_________
Newbie that wants to learn.[/QUOTE]
 32-bit should work just fine on your cpu, i have a 3000 which is exactly the same, just with less cache, and works fine. Perhaps the iso you downloaded (if you did??) had an error or was corrupted in some way. Before burning the iso, check its md5 checksum and compare it to the md5 sum quoted on the download page, it should be exactly the same. In linux you can run in a terminal: "md5sum file.iso" - it may take a while though. There are also md5 checking apps for windows, just use google to find one.

---

### Post by xodeus on 2005-09-09
[QUOTE=~J~]My processor is an AMD64 San Diego 3700.

Have I "GOT" to use the AMD distro, or can I use the i386 version?  I've read somewhere that for most cases, AMD64 users can (and should) use the i386 version.[/QUOTE]
 Of course you can use i386 ubuntu, but if you do, you can't run amd64 optimized apps in that but if you run amd64 version you can then chroot into an 32bit env and run 32 bit apps.
And as you have an AMD64 cpu why don't take it and push it to the limits.

---

### Post by AndrewStout on 2005-09-09
[QUOTE=puppy]Perhaps also worth pointing out that while the 64-bit version of Ubuntu is great,  there are some quite important apps that are still not available, so for the time being, for instance, you won't be able to see flash animations in your webbrowser, read pdf documents etc. 
[/QUOTE]

If I could, I'd like to ask a slightly naive question:  what is the advantage of running the 64-bit version?  I mean, obviously, "more bits must be better", but how much practical performance gain does one get?  (I've got a 3500+ Venice, in case that matters.)

My impression is that 64-bit comes with a lot of headaches--having to deal with chroot and all to run a fully functional web browser, no w32 codecs, etc, etc--obviously 64-bit is the future, but at this point in its development, what do we get in return for that cost?

(I told another forum that I'd just bailed on 64-bit, and a friend told me that was like buying a porche and telling the dealer I didn't care if I couldn't use 5th gear.  I told him it was more like me telling the dealer it's not worth the trouble for me to use 5th gear after he tells me that to use fifth gear on half of the roads that i'll be driving, i'll need to use a different clutch pedal located near the handbrake, and the radio will only pick up AM stations, and to use the headlights I'll have to pop the hood and rewire something, which will make it harder to use the windshield wipers...

Am I really sacrificing 5th gear?  Or am I sacrificing the turbo-boosters that get me from 100mph to 120mph?)

--Andrew

---

### Post by DancingSun on 2005-09-09
Well, the performance benefits of AMD64 applications really depends on the compilers.

The following is the technical bits, you may skip this:
> The x86_64 instruction set architecture (ISA) is essentially the same as the good old x86 ISA (it's a superset of x86).  The only major difference is that it has double the number of registers on the CPU.

CPU registers are storage areas to store numbers.  When more storage is needed than the available registers,  CPU cache will be used.  If the CPU registers and CPU cache are still not enough, the system main memory will be used.  If all these are still not enough, that's where virtual memory/page file on the hard disk comes in.  Needless to say, accessing a registers is faster than any of the other storage areas.

To be able to access these extra registers, however, the source code of the software will have to be compiled with the knowledge of the existence these extra registers.  How well these registers are being used will depend on the compiler itself.

The next release of Ubuntu will be compiled using GCC 4.0, which is likely to be more optimized for the AMD64 architecture.  And thus will yield more performance benefits
With the current batch of programs compiled by GCC 3.3 and 3.4, you'll likely get around 10% performance increase on non-floating point intensive programs.  But with floating point intensive programs, the 64-bit registers on the AMD64 can boost performance as much as around 30%-40%.

The adoption of 64-bit programs will probably not become widespread in the commercial sector until Longhorn...err...Windows Vista is officially released.  Open source software, however, will have a much easier time as anyone can have access to the source code and attempt a recompile.  Although, more compicated programs that has many depedencies will likely have a harder time as the libraries will also need to be recompiled.

References:
[list=1]
[*][http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=1884&p=1](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=1884&p=1)
[*][http://longwood.cs.ucf.edu/~wspires/32bit_versus_64bit_amd64.pdf](http://longwood.cs.ucf.edu/~wspires/32bit_versus_64bit_amd64.pdf)
[/list]

---

### Post by daver68 on 2005-09-09
i've got a AMD Sempron 2800+ laptop coming in soon.

i was just wondering which version of Ubuntu I should install: i386 or the 64-bit?
i figured i'd go with the i386...but it's probably better to get an opinion from people who know Ubuntu very well

(i'm coming from Linspire, so i'm a total newbie with Ubuntu!)

---

### Post by wmcbrine on 2005-09-09
> **AndrewStout]how much practical performance gain does one get?[/quote]The sheer feeling -- I have no benchmarks -- going back and forth between my 32-bit and 64-bit installations, is that 64-bit is very noticeably faster. However, the 32-bit side of my system is an older version of Mandrake with a current kernel, so it's not directly comparable.

> *My impression is that 64-bit comes with a lot of headaches--having to deal with chroot and all to run a fully functional web browser*Not a "fully functional browser" said:**
> *no w32 codecs*I can play most stuff without them. I do have a 32-bit MPlayer in chroot for the rest.

It's not all that difficult to set up chroot.

> *etc, etc*I can't really think of any other issues, myself, except: 1. I couldn't build WINE in 64-bit -- instead, I use chroot; and 2. DOSEmu won't run, in or out of chroot -- apparently the 64-bit Linux kernel doesn't support v86 sessions.

---

