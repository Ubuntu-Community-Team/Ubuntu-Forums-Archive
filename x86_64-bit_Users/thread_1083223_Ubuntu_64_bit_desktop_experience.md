---
title: "Ubuntu 64 bit desktop experience"
date: 2009-02-28
forum: x86 64-bit Users
---

### Post by aryonoco on 2009-02-28
Hi,

I gave 64-bit Linux a try when Athlon 64 first came out, back in 2003. Back then, Debian's AMD64 repo had few packages in it, and the experience was certainly not ready for the desktop. As there was no practical benefit in running a 64-bit OS, I gave it up soon, and have stuck with 32-bit x86 ever since.

However, my next computer will have 4 GB of ram, and for the first time, there is a practical reason to run a 64-bit OS. I am a Ubuntu user now, and I was wondering if there are people running 64-bit Ubuntu here? What's the desktop experience like?

Is the newly-released Adobe flash player usable, or do you still use 32-bit wrappers? what about win32 codecs for things like mplayer? Do the binary drivers for the Atheros wifi chipset and ATI and nVIdia drivers work in 64 bit? What about PulseAudio/Alsa? Do sound problems still persist? Do digital cameras work out of the box with F-spot and the like? What about running Windows XP using virtualbox?

I am aware that there are threads here addressing most of these issues, and I will most certainly look at them once I am hunting for guides on how to set things up. What I am asking here is how do you "feel" about 64-bit Ubuntu vs. 32-bit one, in terms of desktop usage. 

I am yet to be convinced on the merits of 64-bit for normal desktop users, and I have the option of recompiling the kernel of the x86 ubuntu to support more memory, but I feel it might be a good time to see if x86_64 is ready for the desktop; or not.

---

### Post by nss0000 on 2009-02-28
Roughly speaking nothing special It all just works on my "vintage" AMD5400 kit. I've been x64 for two years ... v_8.04 LTS brought everything together. 

I presume Ubuntu will lag a bit against the newer i7/AM-3 kit, but the HW is still 'polishing' anyway. By August I bet any ddr3/cooling/BIOS/driver glitches will be cleaned up and Ubuntu will be without issue pushing lots of new x64 desktop "mainframes" to 28" LCDs.

---

### Post by jespdj on 2009-03-01
64-bit Ubuntu works just as well as 32-bit Ubuntu.

The packages in the Ubuntu repository are 99% the same as in the 32-bit repository. The Flash plug-in in the Ubuntu 8.04 and 8.10 repositories is still Flash 9, 32-bit, with a wrapper. It works without any problems. The 64-bit Flash 10 is not yet out (it's an alpha version right now), but it's not very hard to install and it works well.

One other thing is that until recently there was no 64-bit Sun Java browser plug-in. Sun recently released Java 6 update 12, with a 64-bit browser plug-in. This is going to be included with Ubuntu 9.04 (to be released in April this year). Installing Sun Java 6 update 12 manually is also not that hard, there are a few threads with instructions in this forum.

In normal desktop usage, there's really no difference at all in terms of "feel" compared to 32-bit. You'll notice the difference in the fact that you can use all of your RAM when you have 4 GB or more, and processor-intensive applications might run noticeably faster.

---

### Post by yyyc186 on 2009-03-01
> **aryonoco said:**
> Hi,

I gave 64-bit Linux a try when Athlon 64 first came out, back in 2003. Back then, Debian's AMD64 repo had few packages in it, and the experience was certainly not ready for the desktop. As there was no practical benefit in running a 64-bit OS, I gave it up soon, and have stuck with 32-bit x86 ever since.

However, my next computer will have 4 GB of ram, and for the first time, there is a practical reason to run a 64-bit OS. I am a Ubuntu user now, and I was wondering if there are people running 64-bit Ubuntu here? What's the desktop experience like?

Is the newly-released Adobe flash player usable, or do you still use 32-bit wrappers? what about win32 codecs for things like mplayer? Do the binary drivers for the Atheros wifi chipset and ATI and nVIdia drivers work in 64 bit? What about PulseAudio/Alsa? Do sound problems still persist? Do digital cameras work out of the box with F-spot and the like? What about running Windows XP using virtualbox?

I am aware that there are threads here addressing most of these issues, and I will most certainly look at them once I am hunting for guides on how to set things up. What I am asking here is how do you "feel" about 64-bit Ubuntu vs. 32-bit one, in terms of desktop usage. 

I am yet to be convinced on the merits of 64-bit for normal desktop users, and I have the option of recompiling the kernel of the x86 ubuntu to support more memory, but I feel it might be a good time to see if x86_64 is ready for the desktop; or not.

I've been running 64-bit Ubuntu for over two years now.  I've been a software developer on midrange platforms for over two decades and can tell you the merits "would be" quite high for a 64-bit desktop OS.  The operative phrase being "would be", if opensource developers didn't continue to use tricks in their code which only work on 32-bit platforms.  It's not that the 64-bit version "isn't ready", it's that too many developers out there are still coding with a 32-bit mindset.

Remember that Java slogan, "write once run anywhere"?  fugedaboutit  I cannot tell you the number of sites I encounter (like on-line meeting desktop sharing services) which run an application completely written in Java that works on a 32-bit Ubuntu machine, but not a 64-bit.  Why?  The originating JVM expects the other JVM to be the same, the browser tries to pass 32-bit instead of 64-bit parameters, the list goes on.

I had far fewer problems with OpenSuse 11.0 64-bit than I did with the most recent Ubuntu 64-bit.  If you want to try Ubuntu 64-bit and have it be stable enough for regular business use, you need to stick with Hardy and ignore Ibex all-together.  The new kernel got rolled out without much in the way of testing for the 64-bit platform.  I don't see it getting any better prior to the next major release.

Many people get a significant speed improvement when moving to 64-bit.  Many other people whine and snivel about it being slower.  The difference is in the hardware.  If you bought low end hardware which was designed to run a sucky MS 32-bit OS even though it has a 64-bit chip on it, your performance is going to suck.  There is going to be an awful lot of thunking going on.

If you bought a motherboard+BIOS+CPU+chipset which was designed to run a 64-bit OS, you are going to see some serious improvements.  Yes, the larger pointers take more memory, but disk and video IO happen faster, not to mention calculations.  If you are running a database or using a lot of graphics you should see a significant improvement.  You won't notice squat checking email, surfing the web, and writing a letter to mom.

To get even better performance you need to move away from toy databases like MySQL and try running PostgreSQL.

---

### Post by marcelkoopman on 2009-03-01
> **jespdj said:**
> 64-bit Ubuntu works just as well as 32-bit Ubuntu.

The packages in the Ubuntu repository are 99% the same as in the 32-bit repository. The Flash plug-in in the Ubuntu 8.04 and 8.10 repositories is still Flash 9, 32-bit, with a wrapper. It works without any problems. The 64-bit Flash 10 is not yet out (it's an alpha version right now), but it's not very hard to install and it works well.

One other thing is that until recently there was no 64-bit Sun Java browser plug-in. Sun recently released Java 6 update 12, with a 64-bit browser plug-in. This is going to be included with Ubuntu 9.04 (to be released in April this year). Installing Sun Java 6 update 12 manually is also not that hard, there are a few threads with instructions in this forum.

In normal desktop usage, there's really no difference at all in terms of "feel" compared to 32-bit. You'll notice the difference in the fact that you can use all of your RAM when you have 4 GB or more, and processor-intensive applications might run noticeably faster.
I dont think this is true. Packages are different for platform. Also for instance skype and my webcam dont work on AMD64 while they do in i386. I suspect the skype AMD64 package has a bug thats not existent in the i386 one.

---

### Post by yyyc186 on 2009-03-01
> **marcelkoopman said:**
> I dont think this is true. Packages are different for platform. Also for instance skype and my webcam dont work on AMD64 while they do in i386. I suspect the skype AMD64 package has a bug thats not existent in the i386 one.

You are both correct, you are simply speaking about different things.  The source code for the packages is the same, but due to the 32-bit only tricks some developers put in their code, the compiled and linked executable has bugs in the 64-bit version which do not surface in the 32-bit version.

---

### Post by dcstar on 2009-03-03
> **yyyc186 said:**
> 
.........
If you bought a motherboard+BIOS+CPU+chipset which was designed to run a 64-bit OS, you are going to see some serious improvements.  Yes, the larger pointers take more memory, but disk and video IO happen faster, not to mention calculations.  If you are running a database or using a lot of graphics you should see a significant improvement.  You won't notice squat checking email, surfing the web, and writing a letter to mom.

To get even better performance you need to move away from toy databases like MySQL and try running PostgreSQL.

And if you run VMs then having a 64 bit host seems to help - especially if your VMs are also 64 bit.

BTW, I stuck with my 8.04 64 bit because there just seemed too many hassles with 8.10, I await 9.04 to see if it is as (rock) solid as 8.04.

---

### Post by movieman on 2009-03-04
> **aryonoco said:**
> I am yet to be convinced on the merits of 64-bit for normal desktop users, and I have the option of recompiling the kernel of the x86 ubuntu to support more memory, but I feel it might be a good time to see if x86_64 is ready for the desktop; or not.

All of my Linux machines run 64-bit (Ubuntu or CentOS), even the Atom. The only issue I've had is having to download the beta 64-bit Flash plugin from Adobe to make Flash work in 64-bit Firefox; prior to that I was running 32-bit Firefox instead.

Otherwise, as far as I'm concerned, it just works.

---

### Post by TomB19 on 2009-03-04
I've been using 64 bit Kubuntu 8.10 for a couple of weeks after reverting to 32 bit for the last few years.  My initial 64 bit experience was poor and short lived.

I'll stay with it for a while but I wouldn't make the jump again.  My system is a quad core with 8 GB of RAM so I thought I would benefit from the large memory model.

So far, the differences I've noticed is the very slightly different appearance of the AMD64 version of Kubuntu 8.10 versus the 32 bit version (very, very slightly...  both are KDE 4.1) and the system will sometimes experience pauses for about 15 seconds every minute, or so, when browsing.  When the pauses start, they hang around so I just ditch the machine and jump on a windows box to finish the browsing.  Killing and restarting Firefox does not help.  Rebooting doesn't seem to help, either.

Also, the 64 bit version doesn't seem to multitask as well.  I doubt it's the OS specifically, but the Kubuntu 64 bit distribution.  When I'm encoding video into an ISO with DeVeDe, the system becomes quite sluggish, despite having 4 cores.  On my 32 bit dual core system with 2GB of RAM, it can encode and I still have a smooth desktop.

.... so I wouldn't.  Maybe Ubuntu 64 bit is better.  It wouldn't surprise me.  I'm a KDE guy, though.

---

### Post by jaminux on 2009-03-04
I have been using 64 bit Ubuntu for about 6 months now on my new laptop. Recently I went back to 32 bit for the heck of it because I thought there would not be much performance loss; there was. It was a lot slower. I went back to 64 bit in a flash.

As for packages, well other than Skype I have not ran into any problems.

The new flash player seems to works well for me. I do not look at a lot of flash but I do go on You Tube occasionally and have a look at some flash on sites when necessary. Only problem is the odd website sends to send firefox non-responsive for 10s very very occasionally due to flash. It is not a big problem. No script can help you with that one if you do not want to view the sites flash content.

There were a few minor hitches with the Nvidia drivers when I originally installed Ubuntu. Now they work flawlessly though. As for ATI... who cares? They can never be bothered to put proper Linux support in.

I tried VirtualBox on XP Professional 64 bit and my experience was not good. Everything works except the start menu sends the whole OS non-responsive for about a minute, which is obviously quite major. Might be a 64 bit problem though. P.S. it boots in like 15s though!

I also tried it in VMware Workstation and it worked flawlessly. No problems. I think I am going to buy a copy of their product. Usually I am against spending money on software but there stuff really is good, and worth my time if I want to test software in multiple OSes. It is therefore a VirtualBox problem rather than a visualization problem w/ 64 bit.

Also I didn't try a 32 bit guest, 32 bit guest might be better in VirtualBox.

The merit of 64 bit Ubuntu is really that it is noticeably faster than the 32 bit version, I got aggravated with the speed of the 32 bit version it was that bad in comparison.  

The problems with package availability are now a minor problem rather than a major, at least for me.

---

### Post by yther on 2009-03-04
In my experience, 64-bit desktop is just dandy!  :)

I have run Kubuntu 8.04 and 8.10 on my laptop.  (It's a Dell Inspiron 1520 with 4 GiB of memory.)  8.04 was 32, 8.10 is 64, and they both worked quite well (aside from the not-as-nice-as-it-could've-been KDE 4.1).  Since I changed versions at the same time I changed architectures, any comparisons would be silly.  However, I've had no major problems and everything seems to work well (except certain aspects of printing, that 95% of Ubuntu users will never notice).  Flash works, wireless works, both of which are improvements over 8.04 and most likely unrelated to architecture.

On my desktop, I'm running 64-bit as well.  This box was constructed after some research, to be a Linux powerhouse.  In the near future I will be running two or three simultaneous XP VMs, so I need plenty of memory and processor power.  With 8 GiB of memory and a Q9400 CPU, it pretty much sits here and laughs at me, because I can't throw anything at it to peg the CPU any higher than about 30%.  Flash works, VMWare works, VirtualBox works.  Sound, video, RAID all work nicely.  There's some KDE instability which I attribute to mixing 3.x apps with 4.2, such as Amarok causing Plasma to crash, but the underlying system keeps right on going even when that happens.

So I would say, research your hardware purchases and go for pure 64-bit.  I think you'll like it!  :mrgreen:

---

### Post by jespdj on 2009-03-04
> **marcelkoopman said:**
> I dont think this is true. Packages are different for platform. Also for instance skype and my webcam dont work on AMD64 while they do in i386. I suspect the skype AMD64 package has a bug thats not existent in the i386 one.
Skype is a proprietary program that is not available in the standard Ubuntu repository - not for 32-bit and not for 64-bit.

The [Medibuntu](http://medibuntu.org) repository contains packages for Skype for 32-bit as well as 64-bit Ubuntu. Note that the program itself is still 32-bit, but the package from the Medibuntu repository installs the necessary libraries to make the 32-bit version of Skype run on 64-bit Ubuntu.

Skype with the webcam works fine on my 64-bit 8.04 system.

---

### Post by 3Miro on 2009-03-04
I was triple-booting between 32 bit Kubuntu, 64 bit Kubuntu and WinXP. Now I only have 64 bit Kubuntu ans WinXP and soon I will only have 64 bit Kubuntu.

Skype works just fine, download the .deb file from skype.com and install it --force-architecture. There might be some dependencies that need to be installed, but it works flawlessly on both 64-bit Kubuntu desktop and 64-bit Ubuntu laptop (both are 8.10).

The only issue that I had was the printer, mostly because I just go a cheap one from Walmart (Canon IP1800) instead of researching Linux compatibility. It took some time, but it works just fine.

---

### Post by backtothefuture on 2009-03-04
Any good video cards either Nvidia or Ati that work out of the box.
Will be building a system soon and have decided to go 64 bit. I will running 8 Gb DDR3 ram Intel motherboard Q9400 quad processor. Have not decided on some of the other components yet. I want to run the latest 64 bit Ubuntu. Any suggestions would be appreciated.

---

### Post by marcelkoopman on 2009-03-04
> **backtothefuture said:**
> Any good video cards either Nvidia or Ati that work out of the box.
Will be building a system soon and have decided to go 64 bit. I will running 8 Gb DDR3 ram Intel motherboard Q9400 quad processor. Have not decided on some of the other components yet. I want to run the latest 64 bit Ubuntu. Any suggestions would be appreciated.

I would suggest to take Nvidia graphic cards. I've had a lot of problems with ATI/AMD drivers and the Nvidia drivers are working very well and are updated frequently.

---

### Post by coskierken on 2009-05-01
I just tried Vista64 in Jaunty64 (9.04) and it did not work as well as XP32 Home in VM Workstation.  V64 seemed sluggish.  The XP32 on the other hand was quick and responsive.  I only use it to run my Magicjack with in Linux, so it is not strained at all, and it has very good quality connections.  I will continue testing V64 in VM, but I have reloaded XP32 again, and it works well.  :)

---

### Post by automaton26 on 2009-05-01
I installed Kubuntu AMD64 9.04 last week, on a Dell Studio XPS 435MT, and all these worked perfectly first time:

[LIST]
[*]Latest ATI drivers (from their website)
[*]Firefox, and Flash
[*]MPlayer (Divx)
[*]"wicd" (instead of NetworkManager)
[*]UT2004 x64
[*]Wine
[/LIST]


So IMHO, it's reached the point where it's suitable for new machines, without extra work involved.

---

