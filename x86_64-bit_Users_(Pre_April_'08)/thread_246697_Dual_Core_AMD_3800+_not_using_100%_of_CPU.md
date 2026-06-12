---
title: "Dual Core AMD 3800+ not using 100% of CPU"
date: 2006-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Haegin on 2006-08-29
Hi,
I have just upgraded to a dual core amd x2 3800+ (skt 939) and when i look at the system monitor it shows both cores working but it will only run at the max speed of one core. If one is running at 70% when the pc is being stressed the other will only run at 30%.
It is (amazingly) still faster than my old rig but i did buy it so i could run v fast not a little faster and there is no reason that it can't (other than linux needing more configuration) so I would like to know how to set it all up.

---

### Post by jdong on 2006-08-29
How are you stressing the system? Note that it might be hard disk and not CPU bound?


If you want to test a full CPU load, install the "cpuburn" package (it's in Universe) and run "burnK7" at two terminals.

---

### Post by hajk on 2006-08-29
Any one big programme running will still use only one of the cores -- may be alternating between the two -- unless specifically compiled with multithreading for use on several cores.

That said, why couldn't a big compile run on both cores, just as I used to spread the load with distcc when still using Gentoo?

---

### Post by jdong on 2006-08-29
> **hajk said:**
> 
That said, why couldn't a big compile run on both cores, just as I used to spread the load with distcc when still using Gentoo?
It sure can, just tell make to use -j2 or -j3 or whatever j level you like.

---

### Post by Haegin on 2006-08-30
So, to get this straight, one app will only use the max processing power of 1 core but it will be split over 2 cores, like I am seeing?

I have attached the graph from gnome system monitor. The red line is one core and the yellow line is the other core.

---

### Post by hajk on 2006-08-30
Right, the cores will alternate unless the programme was compiled to use two cores simultaneously (none are in Ubuntu right now). You'll note that the graphs for your two cores are virtually mirror images of one another, indicative of the switching. (Virtually, because some other processes continue to run as well.)

Mind you, several big programmes running simultaneously will be spread over the two cores. This also shows that (in the absence of multithreaded programmes) the advantage of having multiple cores right now is that you can do more things simultaneously, rather than do any one of them faster.

Have fun!

---

### Post by hajk on 2006-08-30
> **jdong said:**
> It sure can, just tell make to use -j2 or -j3 or whatever j level you like.

Of course you're right, me stupid: the Gentoo "rule" for MAKEOPTS was twice the number of CPUs + 1, or "-j 3", but a little higher seemed to work even faster (as far as I recall).

---

### Post by jdong on 2006-08-30
> **hajk said:**
> Of course you're right, me stupid: the Gentoo "rule" for MAKEOPTS was twice the number of CPUs + 1, or "-j 3", but a little higher seemed to work even faster (as far as I recall).

There's a limit to that rule... if you go too high, Linux will waste more CPU time juggling all those compile tasks. If you go too low, there might not be enough jobs to keep all the CPU's fully saturated.

---

### Post by hajk on 2006-08-30
Thanks for bringing me up-to-date on that!

---

### Post by Mau on 2006-09-01
I'm currently looking at this processor and I'm new to the whole dual core thing,  but is there any advantage to having a dual core with Ubuntu right now?  Will I be able to achieve the probably-unrealistic effect of running two 3D games at the same time?

---

### Post by jdong on 2006-09-01
> **Mau said:**
> I'm currently looking at this processor and I'm new to the whole dual core thing,  but is there any advantage to having a dual core with Ubuntu right now?  Will I be able to achieve the probably-unrealistic effect of running two 3D games at the same time?

I don't know if your GPU will do it, but I can tell you that I regularly have a compile job running plus UT2004 at the same time on my core duo, and there's no lag.

If you are a heavy multitasker then dual-core would be right for you... I can't really decide for you whether or not you need dual-core power :)

---

### Post by Mau on 2006-09-01
> **jdong said:**
> I don't know if your GPU will do it, but I can tell you that I regularly have a compile job running plus UT2004 at the same time on my core duo, and there's no lag.

If you are a heavy multitasker then dual-core would be right for you... I can't really decide for you whether or not you need dual-core power :)

Yeah, my GPU would probably explode, but at least my processor wouldn't! :rolleyes:  The compiling example is a good one -- thanks. I'm tempted to go with a dual core just because it isn't too much more, I would probably find a use for it once in a while.

---

### Post by jdong on 2006-09-01
Dual cores are quite cheap nowadays... I'd recommend them. The other bonus is that you can have an app go out of control and it only bogs down one of your CPU's.


P.S. Don't forget about the little buddy we call Pentium D 805.... no it's not a fast CPU by any means but there are some seriously good combo deals with them that can get you a celeron-priced dual core setup :)

---

### Post by Mau on 2006-09-01
> **jdong said:**
> Dual cores are quite cheap nowadays... I'd recommend them. The other bonus is that you can have an app go out of control and it only bogs down one of your CPU's.


P.S. Don't forget about the little buddy we call Pentium D 805.... no it's not a fast CPU by any means but there are some seriously good combo deals with them that can get you a celeron-priced dual core setup :)

First off -- sorry for hijacking this thread!

I've looked at the Intels, but for some reason I got the impression that they don't work as well with Ubuntu for 64bit.  Is that the case?

I'm leaning towards the AM2 socket as that seems to be the future, but I've also read that there are some problems with it.  Is that true?

---

### Post by anindya_m on 2006-09-01
Try a couple of ```
yes > /dev/null &
```commands. This will use up both cores.

---

### Post by jdong on 2006-09-01
> **Mau said:**
> First off -- sorry for hijacking this thread!

I've looked at the Intels, but for some reason I got the impression that they don't work as well with Ubuntu for 64bit.  Is that the case?

I wouldn't say that's true. It is true for the Pentium D series that 64-bit mode doesn't provide as miraculous a speed boost as for AMD chips, but even for AMD chips the performance boosts from blindly switching to 64-bit linux aren't that great.

The Intel Cores are a different story though, the benchmarks show excellent performance all-around.

> 

I'm leaning towards the AM2 socket as that seems to be the future, but I've also read that there are some problems with it.  Is that true?
AM2 is the future if you want high-performance AMD64 chips, but if you're looking at those, IMO Intel Core 2 Duos are a better buy.

---

### Post by RAOF on 2006-09-01
> **Mau said:**
> I'm currently looking at this processor and I'm new to the whole dual core thing,  but is there any advantage to having a dual core with Ubuntu right now?  Will I be able to achieve the probably-unrealistic effect of running two 3D games at the same time?

No, because you can't have 2 games arguing for the same graphics hardware :).

But yes, there is an advantage.  Any time you run more than one thing at once, for example.  Anything **really** processor intensive should also be able to use both cores.

---

### Post by hajk on 2006-09-02
> **RAOF said:**
> 
[snip]  Anything **really** processor intensive should also be able to use both cores.

Only if they're **really** compiled for simultaneous use of multiple cores (multithreading).

---

### Post by Haegin on 2006-09-02
Well I guess this is kind of a cop out but in the end I just switched to gentoo where everything will compile with support for both processors if I set it up right. I have learnt a lot with ubuntu and I will definatly keep using it on other computers but I think gentoo can teach me more in a shorter time now ubuntu has taught me the basics. I have been wanting to try gentoo for a while now and this seemed like the perfect opportunity. If anybody is interested I can post my experiences with gentoo in a few weeks.

---

### Post by jdong on 2006-09-02
> **Human Prototype said:**
> where everything will compile with support for both processors if I set it up right.

Umm, no it won't. Whether or not a program will use 2 processors or not has to do with the way it's programmed, **not** how it's compiled. Gentoo will not use your dual core system any differently than Ubuntu....

---

### Post by hajk on 2006-09-02
> **Human Prototype said:**
>  I have been wanting to try gentoo for a while now and this seemed like the perfect opportunity. If anybody is interested I can post my experiences with gentoo in a few weeks.

Mmm... suit yourself, but a lot of us here are refugees from Gentoo.:wink:

---

### Post by Haegin on 2006-09-02
It will still give me a performance boost as it will be compiled just for my pc once I get all the use flags set up correctly. Also with gentoo I wont have any problems with packages not being built for 64 bit like I do with ubuntu. I am certainly not leaving ubuntu and I think its a great distro. I just have been tempted by gentoo as it seems I may learn more there (I have learnt new things already :D). I will certainly return to ubuntu in the future and it will definatly be the distro I recommend to anybody new to linux. The support for new users is the best I have seen and the community is great.

---

### Post by jdong on 2006-09-02
Go ahead and give Gentoo a shot -- you might like it. But I have to say, I don't think it'll work any better or faster than Ubuntu. I think you have a few misconceptions about Ubuntu vs Gentoo, but I don't want to ruin a good learning experience for you.

Again, wish you a smooth linux experience, whichever distro you choose!

---

### Post by Haegin on 2006-09-02
Don't get me wrong, I'm not expecting that much of a performance boost. I accept that I probably wont notice it. This is more of an excuse than anything but you must admit that some things on 64bit ubuntu are a pain to get working as the binaries just aren't available.

---

### Post by jdong on 2006-09-02
Hmm, usually binaries not being available means that they do not work on 64-bit (like wine,  flash, etc). You need a multiarch capable distro, or a 32-bit chroot environment. I don't think it'll be much different on Gentoo. OpenSUSE is reasonably multiarch, and that might actually get you more software working in 64-bit mode. But for most people, IMO just going 32-bit is the best solution unless you need to use apps that address more than 4GB of RAM.

---

### Post by Kilz on 2006-09-02
You dont need a chroot just to get wine and flash working.
They are also not hard to get working, download a setup script and type in 2 simple commands.

---

