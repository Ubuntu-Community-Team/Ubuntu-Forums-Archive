---
title: "Should I be running Ubuntu 64?"
date: 2008-02-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by shane2peru on 2008-02-02
ok, I have a Pentium D (it has two 32 bit processors).  I have been happily running 32 bit Ubuntu (Currently Gutsy)  and have been happy with it.  I have run Ubuntu for quite some time now, and when I upgraded to a desktop, it never crossed my mind that perhaps I should be running the 64 bit. 
1.  Should I be running the 64bit, is there that much of a difference?  
2.  Are there advantages to it?  
3.  Are there drawbacks?
4.  Is a 32 bit dual processor considered part of the 64 bit family? 

Thanks for the help on this.

Shane

---

### Post by Sh@m@n on 2008-02-02
**4. ** No, you need an amd64 compatible architecture like Core2* Series or AMD64's

---

### Post by shane2peru on 2008-02-02
I'm exposing my ignorance here, so two 32 bit processors is not considered to be a 64bit processor, only the processor that processes 64bits of info at a time?  This has never been really clear to me.  In that case a dual-32bit computer runs fine the 32bit versions of everything, and when one processor get's loaded, it shares its load with the other processor?  Thanks for the quick reply.  

Shane

---

### Post by Neobuntu on 2008-02-02
Dual processors (SMP - Symmetric Multi Processor) Kernels are already covered with the generic 32bit Kernel and distro.

Dual **core** (2 in 1) would be 64-bit (and 1 core **could** be 64bit too) but I'm still using the 32 bit Kernel (disto) for maximum stability and compatibility.  

Any 64bit users want to argue that 64bit kernel status?

Just use Kubuntu (for >= about 384MB RAM); at 3 months (or greater) after it's **last **release (Clean install only. It's 20 minutes), keep it upgraded on-line (within the release) and forget about it. Really! Clean installing every 6 months is the way to go for maximum stability **and** new benefits! Of course, there's no hurry (if you keep upgraded in the release). Just do not rush unless you are **TESTING ONLY**.  Keep your test installs separately! Use self-control. It takes a good amount. No one will stop you, so don't do it to fast.

I'm NOT a fan of managed dist-upgrade and release conversion to the next release. Even if you're lucky it's still not better. It's about the foundation, being fundamental (and your time saved). Backup and restore (of your stuff) is easier with Kubuntu. Always backup!

---

### Post by johnficca on 2008-02-02
If its a Pentium D dual-core then yes, you can and should run 64 bit ubuntu, I have the same cpu and ubuntu does run a little faster with the 64 bit version.

---

### Post by shane2peru on 2008-02-02
> **johnficca said:**
> If its a Pentium D dual-core then yes, you can and should run 64 bit ubuntu, I have the same cpu and ubuntu does run a little faster with the 64 bit version.

Ok, the sticker says, Pentium D, that is it.  However I know it has two processors, I have seen it several times, once while installing Gentoo, and another time.  Ok, I found it, I clicked on the system monitor on my panel and click on the system tab and here is what it says:```
Hardware
Memory:  493.2 MB
Processor 0: Intel(R) Pentium(R) D CPU 3.00GHz
Processor 1: Intel(R) Pentium(R) D CPU 3.00GHz


```

Sooo, I know I have two processors.  Does that make it a dual-core?  I'm sorry I really don't know what it is.

Shane

---

### Post by Dark Hornet on 2008-02-02
> **shane2peru said:**
> Ok, the sticker says, Pentium D, that is it.  However I know it has two processors, I have seen it several times, once while installing Gentoo, and another time.  Ok, I found it, I clicked on the system monitor on my panel and click on the system tab and here is what it says:```
Hardware
Memory:  493.2 MB
Processor 0: Intel(R) Pentium(R) D CPU 3.00GHz
Processor 1: Intel(R) Pentium(R) D CPU 3.00GHz


```

Sooo, I know I have two processors.  Does that make it a dual-core?  I'm sorry I really don't know what it is.

Shane

Just because this shows that you have a Processor 0 and 1, does not necessarily mean that you have two processors or it is a dual core chip.  I have a P4 3.6 in one of my boxes, and it has "Hyper-Threading" which SIMULATES a second CPU.  When I take a look at my specs on Ubuntu, sure enough it tells me I have two processors, but in reality all I have is one CPU that simulates two processors.  Now I am not sure what the Pentium D does, but usually with Intel, if it is a true dual core, then it usually will tell you....just a thought.

---

### Post by shane2peru on 2008-02-02
> **Dark Hornet said:**
> Just because this shows that you have a Processor 0 and 1, does not necessarily mean that you have two processors or it is a dual core chip.  I have a P4 3.6 in one of my boxes, and it has "Hyper-Threading" which SIMULATES a second CPU.  When I take a look at my specs on Ubuntu, sure enough it tells me I have two processors, but in reality all I have is one CPU that simulates two processors.  Now I am not sure what the Pentium D does, but usually with Intel, if it is a true dual core, then it usually will tell you....just a thought.

Ok, you have forced me to bring out the heavy ammo.  After searching around a while I finally dug out the box that my processor came in.  It says Intel Core 2 Duo Processor.  I didn't think it was that complex of an issue.  I'll search the web now that I know what it is called, and see if it is 64bit or not.  I'm sure Google will have the answer.  Thanks for the help.

Shane

---

### Post by Dark Hornet on 2008-02-02
--cool...from what I understand, I though all of the Core Duo Chips where 64 bit...I could be wrong...anyway...good luck!

---

### Post by shane2peru on 2008-02-02
ha ha, I searched the forums several times with the search button at the top, but then googled and found this thread:  

[http://ubuntuforums.org/archive/index.php/t-330655.html](http://ubuntuforums.org/archive/index.php/t-330655.html)

Long story short, the Core Duo is symantics and is only a 32bit processor, the Core 2 Duo is actually a 64bit processor.  So yes according to that thread I should use the 64bit Ubuntu version, also I found this thread, that was extremely technical and unclear:  [http://www.hardwareinreview.com/processors/the_intel_core_2_duo_processor.html](http://www.hardwareinreview.com/processors/the_intel_core_2_duo_processor.html)

Perhaps someone more technical than I would understand all that stuff.

Shane

---

### Post by shane2peru on 2008-02-02
> **Dark Hornet said:**
> --cool...from what I understand, I though all of the Core Duo Chips where 64 bit...I could be wrong...anyway...good luck!

Somehow my post got above yours, and was posted after yours.  Thanks for the help!  I'm downloading the 64bit version now.  I will run it on a test partition first and see how it goes.  I have my home on a separate partition, and since it is the same OS (in reality) if I just use the same username etc, would that affect my home partition and config files for FireFox or others?  Thanks.

Shane

---

### Post by Dark Hornet on 2008-02-02
It shouldn't effect anything, but personally, I would have a separate log in name and password for your 64 bit partition just to keep things straight in your own mind.  I know I might get confused...lol.

---

### Post by shane2peru on 2008-02-02
> **Dark Hornet said:**
> It shouldn't effect anything, but personally, I would have a separate log in name and password for your 64 bit partition just to keep things straight in your own mind.  I know I might get confused...lol.

True!  I think I will do that.  That way if there is a problem I won't mess up my home folder.

Shane

---

### Post by DJiNN on 2008-02-03
> **shane2peru said:**
> Long story short, the Core Duo is symantics and is only a 32bit processor, the Core 2 Duo is actually a 64bit processor.  So yes according to that thread I should use the 64bit Ubuntu version.



I think the key thing to remember here is not that you "Should" but that you "Can" if you want to. 64bit processing is great & i would recommend it to anyone that has capable hardware, but there will always be bumps along the way just as in your chosen 32 bit OS. 

It's your choice, and if you have a 64bit Live CD then stick it in & boot up..... if your systems capable of uisng it then it'll boot, otherwise it won't. :)  Also, if you do decide to install, you'll have to do a complete fresh install obviously, and that includes your /home partition. You can use the same physical /home of course, but NOT any of the configs etc that you were using for your 32 bit OS. All i did when i went from 32 to 64, was copied my whole /home dir to another partition, then installed the 64 bit OS, then just moved all my personal data into the new /home...... no problems. 

I use Xubuntu 64 bit & it's fantastic (On a Core 2 Duo laptop). I hope you enjoy it, and please share how you get on.

---

### Post by shane2peru on 2008-02-03
> **DJiNN said:**
> I think the key thing to remember here is not that you "Should" but that you "Can" if you want to. 64bit processing is great & i would recommend it to anyone that has capable hardware, but there will always be bumps along the way just as in your chosen 32 bit OS. 

It's your choice, and if you have a 64bit Live CD then stick it in & boot up..... if your systems capable of uisng it then it'll boot, otherwise it won't. :)  Also, if you do decide to install, you'll have to do a complete fresh install obviously, and that includes your /home partition. You can use the same physical /home of course, but NOT any of the configs etc that you were using for your 32 bit OS. All i did when i went from 32 to 64, was copied my whole /home dir to another partition, then installed the 64 bit OS, then just moved all my personal data into the new /home...... no problems. 

I use Xubuntu 64 bit & it's fantastic (On a Core 2 Duo laptop). I hope you enjoy it, and please share how you get on.

Really!  So all of the config files are 32 or 64 bit sensitive?  I have my /home directory on a separate partition so doing a clean install is basically a no issue.  Thanks for the tip though, I will have to erase all my config files, and transfer everything.  However I'm going to install it on a separate partition and dual boot with 32 bit and 64bit and see what the difference is.  Thanks again.

Shane

---

### Post by DJiNN on 2008-02-03
> **shane2peru said:**
> Really!  So all of the config files are 32 or 64 bit sensitive?  I have my /home directory on a separate partition so doing a clean install is basically a no issue.  Thanks for the tip though, I will have to erase all my config files, and transfer everything.  However I'm going to install it on a separate partition and dual boot with 32 bit and 64bit and see what the difference is.  Thanks again.

Shane

Hi Shane.

Yes, as far as i'm aware, and it makes sense i guess, as there are so many things that are obviously different about the two architectures, ie: all progs have to be re-compiled to work properly etc. 

I know that you can run 32 bit apps on a 64 bit system, because i'm doing it here, but i'm guessing that those 32 bit apps are re-compiled to be able to do that. I'm no expert by any means, and i could be wrong, but it makes a lot of sense and i think the way you're going about it with the whole "Dual Boot" scenario is perfect, because you're preserving all your data & your 32 bit OS, should anything go wrong, while you try out the new 64 bit OS. :)

I think (hope) you'll like it...... 64 bit is definitely the way to go, and we should have been there a few years ago really, because the hardware was available. A lot of people say that there's no discernible  difference between 32 & 64bit, but all of the 64 bit OS's i have used have been a LOT faster & snappier than their 32 bit counterparts, and that's just in normal "Day 2 Day" use..... of course, as in all things, it's your own opinion that counts. :)

---

### Post by sandysandy on 2008-02-03
joining the discussion late.

i am using Ubuntu Gutsy 7.10  64 bit on my Pentium D 3.00GHz 1 GB RAM  machine with no problems whatsoever. i used the alternate CD (Edubuntu) for the installation. 
The Ubuntu 64 bit live CD  works fine for live booting but gave me problem while installing to hard disk so i used alternate CD for installing to Hdd.

 It is definitely a good idea as proposed above to first test the live CD of 64 bit for compatibility.

regards

---

### Post by fourthofjuly on 2008-02-03
Even I have a Dual core processor:

Intel Dual Core Pentium D

I have a 64-bit Ubuntu live CD that won't run on my machine.

You need Core 2 Duo / AMD64 processor which are actually 64-bit processors.

Correct me if I am wrong...

---

### Post by Yellow Pasque on 2008-02-03
Sorry I didn't respond sooner, but if you're already running Gutsy32, the easiest way is:
```
cat /proc/cpuinfo
```

---

### Post by DJiNN on 2008-02-03
> **sandysandy said:**
> joining the discussion late.

i am using Ubuntu Gutsy 7.10  64 bit on my Pentium D 3.00GHz 1 GB RAM  machine with no problems whatsoever. i used the alternate CD (Edubuntu) for the installation. 
The Ubuntu 64 bit live CD  works fine for live booting but gave me problem while installing to hard disk so i used alternate CD for installing to Hdd.

 It is definitely a good idea as proposed above to first test the live CD of 64 bit for compatibility.

regards

Hi sandysandy.

I didn't even know there was a 64bit Edubuntu ed....? That's great. :)  I haven't tried any other install myself, apart from the standard Live CD routes, but i'm looking forward to doing so sometime soon, even if it's just to see how it goes & what i end up with.  

Hope you're enjoying your 64bit Ubuntu? Do you find much difference overall between the 64bit Ubuntu & the 32 bit version?

---

### Post by Yellow Pasque on 2008-02-03
> **fourthofjuly said:**
> Even I have a Dual core processor:
Intel Dual Core Pentium D
I have a 64-bit Ubuntu live CD that won't run on my machine.
You need Core 2 Duo / AMD64 processor which are actually 64-bit processors.
Correct me if I am wrong...

You're wrong: Pentium D supports EM64T. You also need a 64-bit compatible motherboard.

---

### Post by DJiNN on 2008-02-03
> **Temüjin said:**
> Sorry I didn't respond sooner, but if you're already running Gutsy32, the easiest way is:
```
cat /proc/cpuinfo
```

That's great, thanks for the info, but it comes up with the following here, which is misleading as it indeed looks as though you have 2 CPU's. :)

```
 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.60GHz
stepping        : 9
cpu MHz         : 2593.893
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5191.66
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.60GHz
stepping        : 9
cpu MHz         : 2593.893
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5187.75
clflush size    : 64

```

This is my main (32 bit) machine running Mint 4 (Gnome).  To the uninitiated it can look as though it does indeed have 2 Processors. :)

---

### Post by DJiNN on 2008-02-03
> **Temüjin said:**
> You're wrong: Pentium D supports EM64T. You also need a 64-bit compatible motherboard.

Hmmm, that's interesting. I'm going to try a 64 bit OS on this machine just to see what happens (Live CD of course).

Thanks for the info.

---

### Post by Yellow Pasque on 2008-02-03
> **Temüjin said:**
> Sorry I didn't respond sooner, but if you're already running Gutsy32, the easiest way is:
```
cat /proc/cpuinfo
```
I should be more specific. Look for the long mode (Lm) flag.

---

### Post by shane2peru on 2008-02-03
> **Temüjin said:**
> You're wrong: Pentium D supports EM64T. You also need a 64-bit compatible motherboard.

Actually if it is a Core Duo it is only 32 bit, if it is a Core **2** Duo then it  is a 64 bit processor.  That is according to this article:  [http://www.hardwareinreview.com/processors/the_intel_core_2_duo_processor.html](http://www.hardwareinreview.com/processors/the_intel_core_2_duo_processor.html)

It is a poor naming IMHO by Intel, and very confusing obviously.  Now I don't about the Pentium D stuff, perhaps if it is a Pentium D it is a Core **2** Duo.  That little number makes all the difference.  It is my understanding that it has 2 32bit processors therefore making it a 64bit machine, but I'm not 100% on that.

BTW, I'm posting from my 64bit partition, getting programs installed etc right now, I will run it through it's paces later do some of my labour intensive work and see how it holds up.  Seems normal to me right now.  Thanks for all the info!

Shane

---

### Post by Yellow Pasque on 2008-02-03
> Now I don't about the Pentium D stuff, perhaps if it is a Pentium D it is a Core 2 Duo. That little number makes all the difference. It is my understanding that it has 2 32bit processors therefore making it a 64bit machine, but I'm not 100% on that.

No, two 32-bit cores do not make a 64-bit CPU. The Pentium D's I'm referring to are the ones based on the Netburst architecture, Smithfield (Pentium D 8xx) and Presler (Pentium D 9xx) cores. What's confusing is that Intel now calls some of their C2D's Pentiums.

---

### Post by shane2peru on 2008-02-03
> **Temüjin said:**
> No, two 32-bit cores do not make a 64-bit CPU. The Pentium D's I'm referring to are the ones based on the Netburst architecture, Smithfield (Pentium D 8xx) and Presler (Pentium D 9xx) cores. What's confusing is that Intel now calls some of their C2D's Pentiums.


OK, I don't know about all that stuff.  It is not the first time that Intel made a naming error.  I read in one of those articles that they had naming problems before, and their customers didn't understand the new system.  They may make good processors, however their customer relations is lacking.  :lolflag:  Unless you really get into the technical stuff of building computers, it probably isn't going to be that necessary to know all that stuff ;)  at least for me it isn't, now I know I have a 64bit, and hope all this info will help further users that are in doubt.

Shane

---

### Post by sandysandy on 2008-02-03
> **DJiNN said:**
> Hi sandysandy.

I didn't even know there was a 64bit Edubuntu ed....? That's great. :)  I haven't tried any other install myself, apart from the standard Live CD routes, but i'm looking forward to doing so sometime soon, even if it's just to see how it goes & what i end up with.  

Hope you're enjoying your 64bit Ubuntu? Do you find much difference overall between the 64bit Ubuntu & the 32 bit version?

hi DJiNN

64 bit ubuntu is good. In fact i have not run the 32 bit version so far.
the alternate CD is a breeze to set up.

regards

---

### Post by NightwishFan on 2008-02-03
64-bit is more stable but less compatible, (In this coming year most software will have added 64bit compatibility and the speed gain is noticeable)

---

### Post by Yellow Pasque on 2008-02-03
> **NightwishFan said:**
> 64-bit is more stable but less compatible, (In this coming year most software will have added 64bit compatibility and the speed gain is noticeable)

I'm not quite sure why you say 64-bit is more stable. It should have the same stability, because most programs will be compiled from the same code. (That's the point of writing portable software, compatibility across platforms). The same thing goes for compatibility. Very few programs are 32-bit only, and it's not a big issue since you can run 32-bit programs.

---

