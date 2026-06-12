---
title: "x86_64 Kernel with heavy loads, how does it behave for you?"
date: 2008-05-10
forum: x86 64-bit Users
---

### Post by | MM | on 2008-05-10
Hi,

during the development period of Ubuntu Hardy, i was using the 32bit version of Ubuntu.  Post-release i installed a fresh copy of Ubuntu Hardy 64bit.  

I have since noticed that the 64bit kernel doesn't behave as gracefully under high cpu loads as its 32bit counterpart. 

For instance, during the installation of package updates and the like, my system can become unusable (music crackles or stops, mouse pointer can freeze (intermittently) i.e. general unpleasantness...) for the duration of the update while the package manager does what it does.

Are other people experiencing this?  The 32bit kernel seemed to multi-task allot better than the current 64bit ubuntu kernel.

Is there anything i can tweak, short of recompiling a new kernel?  Or, if others a seeing similar behaviour, could someone with some kernel/system knowledge help file a bug?


Regards,
Matthew

---

### Post by tenmoi on 2008-05-10
Yes, I experienced the same problem as you until I updated the kernel to 2.6.24.17. This one is stabler and can  withstand heavy load. ON my machine the default 64 bit kernel would crash if subjected to heavy load. You could enable the proposed repository to install this new kernel.

ONe reminder, though, you will have to recompile some of your propramme modules if you so did with the previous kernel.

---

### Post by Yellow Pasque on 2008-05-11
I have been using the vanilla kernel.org 2.6.24 kernel since its rc4 incarnation and have been very pleased with it. The other day, I finally got around to updating from 2.6.24 to 2.6.24.7

If you let me know what hardware you have and/or plan to use (i.e. with lshw or lspci), I can help you with configuring and installing the kernel.

Also, for the sound, I would suggest looking into OSS4 (see link in my sig).

---

### Post by insane_alien on 2008-05-11
my machine functions fine under heavy loading(~5.6 for 96 hours) no problems at all.

---

### Post by Em-Buntu on 2008-05-11
I've been running 64-bit version on my AMD Opteron system with no problem.
With 10-12 windows and apps running, I usually see no more then 30% utilization. 
This is while watching a video, with evolution and Firefox open, and downloading with Deluge amonst other things.

I did see unusally high CPU usage and slow operation when I had Gutsy & Hardy Ubuntu installed on an older ATA100 hard drive. Switching to a newer ATA133 hard drive fixed the problem.
Now everythings running...sweet!

---

### Post by Jouke74 on 2008-05-11
@Topic starter: What hardware do you have? 
And what do you mean by load, what programs are running?

Compiz? Tracker? e.g.

Your problem can be split into three things I guess. One, processor load, does it use 100%? Two, harddisk load, and here is where the package manager makes a big difference. Three memory load.

---

### Post by lefterist on 2008-05-11
As of the past week, I have 2 C2D/Q x86_64s I am testing. One with 60-70% load, and the other 95-100 all day long. So far they are both performing rock solid for the past week. The only problem I faced was with the non supported driver of ATI. Once I removed it, everything worked well ever since.

---

### Post by Em-Buntu on 2008-05-11
^Yes, I agree. 
I choose not to enable the ATI proprietary driver either. The default open source driver is working just fine on my x1800, so I didn't want to risk hosing the system.

---

### Post by Jouke74 on 2008-05-12
Well I choose to enable the ATI driver. All things are also working fine Raedon X1600 here. 3 or 4 days with full load on a 4200 AMD X2 with Seventeen Or Bust (Prime detection) without any issues. 

It's the things he's running, as there is a fulll load in many ways.

---

### Post by | MM | on 2008-05-17
> **Jouke74 said:**
> @Topic starter: What hardware do you have? 
And what do you mean by load, what programs are running?

Compiz? Tracker? e.g.

Your problem can be split into three things I guess. One, processor load, does it use 100%? Two, harddisk load, and here is where the package manager makes a big difference. Three memory load.

AMD64 3000, 512 MB ram, Nvidia GF6600, Realtek AC97 SOund.

More than two io intensive activity really... for instance Package manager doing something (reading package db) while Rhythmbox is playing/watching my Music folder.

---

### Post by Kilz on 2008-05-18
> **| MM | said:**
> AMD64 3000, **[COLOR="Red"]512 MB ram[/COLOR]**, Nvidia GF6600, Realtek AC97 SOund.

More than two io intensive activity really... for instance Package manager doing something (reading package db) while Rhythmbox is playing/watching my Music folder.

I think the issue will be obvious to many. 512 is a minimum amount of ram for a 64bit system. It will be fine when running 1 or 2 things. But under heavy load it will be a problem.

---

### Post by Jouke74 on 2008-05-18
Yeah, if rhythm box and the package manager are already a problem, which is not really a heavy load in my opinion, it's time to stick in more memory. Funny enough I am using about 400 megs in general, under heavy load...

---

### Post by | MM | on 2008-05-18
> **Jouke74 said:**
> Yeah, if rhythm box and the package manager are already a problem, which is not really a heavy load in my opinion, it's time to stick in more memory. Funny enough I am using about 400 megs in general, under heavy load...

Oh ok... guess i'll get some memory then.  

I still can't believe there such a big difference between the 32bit kernel and the 64bit in terms of behaviour under load.

---

### Post by jocko on 2008-05-18
> **| MM | said:**
> Oh ok... guess i'll get some memory then.  

I still can't believe there such a big difference between the 32bit kernel and the 64bit in terms of behaviour under load.

If I have understood it correctly 64 bit will use a little bit more memory than 32 bit, which means that if you have a limited amount of memory it will probably fill up sooner on a 64 bit system, leading to more swapping and general poor performance.
But with more memory 64 bit should perform better than 32 bit.

---

### Post by Julius on 2008-05-18
mmm for some reason it's working better now than when I first installed hardy, even though I havent updated the kernel or anything.

Yesterday I was compiling firefox while doing other things and everything worked fine.

---

### Post by markbuntu on 2008-05-18
I just installed the x86_64 Kernel on my machine this morning by accident. Put the wrong cd in the player. Thought I would give it a spin.

It seems far better than 386i as far as cpu loading goes. I am using the ATI propietary driver v8.47.3 from the Ubuntu repository and have much better performance, even with compiz actions like spinning the cube using indirect rendering while running a stream in rythmbox I do not get cpu loading above about 80%. Most of the time it is below 20%.

I will see how it does with video later and update this post

HP 1330n Media Center (modified)
ASUS A8AE-LE motherboard (OEM)
AMD Athlon64 3800+ 2.9GHZ 939 socket
3GB 3200 DDR RAM
ATI Radeon Express 200M (disabled in bios)
ATI HD3650 1GB DDR2  PCI Express
AC97 on board sound
Realtek 810L

SOYO 24 inch LCD wide screen monitor 1920x 1200
Samsung 930B 19 inch LCD 1280x1024

ATI Proprietary Linux Driver Version Identifier:8.47.3
Big Desktop, Compiz, Emerald

fgl_glxgears ~10000
glxgears ~4400
Compiz Benchmark ~ 110
 while streaming in rythmbox

Update:
Flash video from youtube runs about 95-98% cpu usage in full screen but only about 60% in a window. Ram use is right about 1.050GB.
So it seems that less than 1GB ram will cause problems.
Google Earth next...stand by...

---

### Post by | MM | on 2008-05-20
I saw a post on planet.ubuntu about the same bug i was seeing.  So I know the problem now and its not just me!  :)

Here's the planet post: [http://www.sharms.org/blog/?p=144](http://www.sharms.org/blog/?p=144)
And here's the Luanchpad bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226)

Its to do with a bug in the scheduler, something to do with the way the CFS has been setup in Ubuntu. the current server kernel or the kernel in hardy-proposed fixes the problem, according to the links.

I will hold out until it becomes and official release so i dont blindly walk into restricted modules issues.

---

### Post by jpkotta on 2008-05-26
No need to wait, the fix is available now.  Add the hardy-proposed repositories for main and restricted to /etc/apt/sources.list and update to the latest kernel.

---

