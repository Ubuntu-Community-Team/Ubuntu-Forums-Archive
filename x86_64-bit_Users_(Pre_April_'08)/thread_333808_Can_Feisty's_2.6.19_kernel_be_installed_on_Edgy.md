---
title: "Can Feisty's 2.6.19 kernel be installed on Edgy?"
date: 2007-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by rickross on 2007-01-07
I have a Core2Duo machine with Edgy for AMD64 installed, and I would like to switch to a 2.6.19 kernel instead of the 2.6.17 that Edgy includes. My Asus P5B-VM motherboard uses an Intel 965 chipset, and I think it may be better supported under 2.6.19 than under 2.6.17.

I saw good instructions at howtoforge.com about how to build a kernel from source for Ubuntu, but I'm wondering whether I could simply download "linux-image-2.6.19-7-generic" from the Feisty repository and install it directly? ([http://packages.ubuntu.com/feisty/base/linux-image-2.6.19-7-generic](http://packages.ubuntu.com/feisty/base/linux-image-2.6.19-7-generic))

Is this a reasonable way to get the updated, Ubuntu-patched kernel from Feisty without having to go for the whole Feisty release? It would not be comfortable to use Feisty instead of Edgy, but I'd very much like to have some of the improved kernel support for my Intel 965 mobo.

What do you think? Is it OK to just grab the package and install it, or is it necessary to build from source? If from source, would it be better to use the Feisty source package, or just get the generic source from kernel.org?

Thanks,
Rick

---

### Post by rickross on 2007-01-08
I guess I decided to answer my own question by experimenting. I went ahead and installed the 2.6.19-7 kernel from Feisty, and everything seems to be running smoothly so far. This may end poorly, but so far, so good.

I think I will try to build this patched kernel from the source package anyway, so I can add some additional config options and still have the various Ubuntu-specific patches included. Has anyone else done this? Is it basically the same as building from the kernel.org sources except that you use the source form the Ubuntu package file instead?

Rick

---

### Post by xopher on 2007-01-08
> **rickross said:**
> I guess I decided to answer my own question by experimenting. I went ahead and installed the 2.6.19-7 kernel from Feisty, and everything seems to be running smoothly so far. This may end poorly, but so far, so good.

I think I will try to build this patched kernel from the source package anyway, so I can add some additional config options and still have the various Ubuntu-specific patches included. Has anyone else done this? Is it basically the same as building from the kernel.org sources except that you use the source form the Ubuntu package file instead?

Rick

Here's a wiki page describing the process:

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

---

### Post by pross on 2007-01-08
could you supply some links to the files you downloaded?

2.6.19 includes support for my motherboard for temp monitoring :)

---

### Post by Biker on 2007-01-09
This is what I did;

1. backup /etc/apt/sources.list
2. replace temporary (!) all edgy with feisty in sources.list
3. apt-get update
4. apt-get install linux-headers-2.6.20-5 linux-headers-2.6.20-5-generic linux-image-2.6.20-5-generic
5. check /boot/grub/menu.lst, mine was set to hd(0,6) and /dev/sda7 and were wrong. It must be hd(0,1) and /dev/sda2
6. restore your /etc/apt/sources.list from step 1
7. reboot

I must recompile my nVidia drivers and VMware Server modules too;

[http://www.ubuntuforums.org/showthread.php?t=334394&highlight=vmware+server+feisty](http://www.ubuntuforums.org/showthread.php?t=334394&highlight=vmware+server+feisty)

---

### Post by frigaut on 2007-01-14
Biker/rickross: Still running fine? Noticed anything annoying? What about drivers (e.g. fglrx or madwifi)?

---

### Post by BIGtrouble77 on 2007-01-14
This is a great idea.  In theory I can't see why this could cause any permanent damage as you can always go back to your original kernel.  

I'm using dapper and I might give fiesty's kernel a shot as well.  I do have a quick question... Do you use the nvidia proprietary driver?  If you do, are there restricted drivers available for the latest fiesty kernel?  I just want to know what troubles you had to deal with in getting your video drivers working.  This is the only thing i'm worried about.

-BT

---

### Post by superm1 on 2007-01-14
> **BIGtrouble77 said:**
> This is a great idea.  In theory I can't see why this could cause any permanent damage as you can always go back to your original kernel.  

I'm using dapper and I might give fiesty's kernel a shot as well.  I do have a quick question... Do you use the nvidia proprietary driver?  If you do, are there restricted drivers available for the latest fiesty kernel?  I just want to know what troubles you had to deal with in getting your video drivers working.  This is the only thing i'm worried about.

-BT
More than likely, you will be able to install linux-restricted-modules for feisty as well.

---

### Post by BIGtrouble77 on 2007-01-14
Biker, I did the update and the kernel works (I opted for the low latency version), but when I go to install the headers it wants to update half my system.  I don't want to update things like GCC 4.1 because that's gonna cause so many headaches.  Did you just let it update everything, or is there a way to just force it to install only the headers?  Maybe I have so many updates because I'm still using dapper.

-BT

---

### Post by factor on 2007-01-15
how did you recompile nvidia? i tried to install downloaded drivers, as usual, but after upgrading kernel following the instructions i run the nvidia installer and i get that there is no valid GCC for compiling, i tried export CC=gcc-4.1 (and gcc-4.0, gcc-3.4 and gcc) and i get the same error, except it says it changes the version name (so the export works). Detail tho, when installing kernel i got updated libc6 too.

In the other hand i tried to use nvidia-glx from feisty repo but it crashes.

I hope someone can answer me. I need nvidia driver only for dual monitor setup with one card.

Regards.

---

### Post by UBfusion on 2007-01-16
@rickross: I have also P5B-VM. It's a very nice mobo with excellent chipsets and great possibilities imho not yet exploited fully by Ubuntu.

I am struggling **every day** with the daily builds of Feisty because I really need proper and full HD Audio support (with bit-perfect spdif out, Dolby Digital and all).

HD Audio did work splendidly in one installation of Edgy I managed to to a month ago (and which I cannot reproduce no matter what (btw how did you manage to install Edgy 64? installing from iso does not work either).

Since installing Feisty 64 on P5B-VM from an iso is still impossible on this specific motherboard (tried most builds, pre- and post- Herd2), the solution you provide has great potential.

All P5B-family owners would greatly appreciate if you could reiterate in more detail the steps for a safe for newbies way to reproduce what you did (2 months ago I tried to upgrade alsa which in turn required a kernel upgrade which blew my system and I could not go back).

Hopefully this thread will serve as a kind of a HOW-TO for HD Audio in amd64 and thus make all audiophiles out there drool over Ubuntu... (needless to say Windows 64 are pathetic on P5B-VM, just have a look at the Asus vip forum).

---

### Post by superm1 on 2007-01-16
> **UBfusion said:**
> @rickross: I have also P5B-VM. It's a very nice mobo with excellent chipsets and great possibilities imho not yet exploited fully by Ubuntu.

I am struggling **every day** with the daily builds of Feisty because I really need proper and full HD Audio support (with bit-perfect spdif out, Dolby Digital and all).

HD Audio did work splendidly in one installation of Edgy I managed to to a month ago (and which I cannot reproduce no matter what (btw how did you manage to install Edgy 64? installing from iso does not work either).

Since installing Feisty 64 on P5B-VM from an iso is still impossible on this specific motherboard (tried most builds, pre- and post- Herd2), the solution you provide has great potential.

All P5B-family owners would greatly appreciate if you could reiterate in more detail the steps for a safe for newbies way to reproduce what you did (2 months ago I tried to upgrade alsa which in turn required a kernel upgrade which blew my system and I could not go back).

Hopefully this thread will serve as a kind of a HOW-TO for HD Audio in amd64 and thus make all audiophiles out there drool over Ubuntu... (needless to say Windows 64 are pathetic on P5B-VM, just have a look at the Asus vip forum).
Well I can put some comments here about HD audio and edgy.

Xine based products (totem-xine,xine-ui, gxine) have a bug that as the content progresses, the audio lags the video more and more.  This only happens to me when I have an AC3/DTS stream with SPDIF.  There is a workaround, but its still not exact.  Earlier builds of xine based products worked as expected.

VLC has a bug with every version beyond 0.8.4a that SPDIF is very choppy.  This means the 0.8.6svn version in edgy, as well as the 0.8.6 final version in feisty.  Even the 0.8.4 release in dapper is broken.  My solution in the interim has been to do a build of 0.8.4a and use that.  I can build it for amd64/edgy if you would like.

---

### Post by bahrain on 2007-01-29
good idea

---

### Post by mlissner on 2007-02-01
Well, this is a phenomenal idea. I just thought of it myself, decided to look it up, and lo and behold, I'm a step behind. Thanks for the tutorial. After five minutes of running the new kernel, all seems well.

I also installed the restricted packages and finally got my intel abg3945 card to work.

---

### Post by bahrain on 2007-02-01
> **mlissner said:**
> Well, this is a phenomenal idea. I just thought of it myself, decided to look it up, and lo and behold, I'm a step behind. Thanks for the tutorial. After five minutes of running the new kernel, all seems well.

I also installed the restricted packages and finally got my intel abg3945 card to work.
but be careful

the latest stable release is 2.16.19 and after following this tutorial you will install 2.16.20 which it is just a release candidate.

for more information
[www.kernel.org](www.kernel.org)

---

### Post by pseudonym on 2007-02-01
I run a 2.6.19 kernel from kernel.org, with ['ck' patches]("http://members.optusnet.com.au/ckolivas/kernel/"). This is a much safer way to run a recent kernel on Edgy - no requirement to upgrade half your system with all the potential headaches that brings. No Ubuntu patches either, but TBH I've always found hand-compiled kernels from kernel.org to be more stable.

---

### Post by mlissner on 2007-02-01
> **bahrain said:**
> but be careful

the latest stable release is 2.16.19 and after following this tutorial you will install 2.16.20 which it is just a release candidate.

for more information
[www.kernel.org](www.kernel.org)

Yeah, but over on gentoo everybody's installing this kernel, and anyway, unless there's some grievous issue with it, I'm assuming it's relatively safe.

Anyway, upgrading has fixed my suspend problem while still supporting the rest of my hardware, which is nothing short of phenomenal.

---

### Post by mlissner on 2007-02-02
Disregard this...internet is weird sometimes...

---

### Post by homerh on 2007-02-02
Hiya 
 Im running 2.6.20 for a while now(about a month) without any problem and ive installed all the libc and gcc stuff :) 
the only problem i have is with vmware and needing to patch the vmmod:( 



best regards ):P

---

### Post by factor on 2007-02-13
hi, how can i get updates without "upgrading" the kernel to 2.6.17.11 ?

thanks in advance for your help.

Regards.

---

