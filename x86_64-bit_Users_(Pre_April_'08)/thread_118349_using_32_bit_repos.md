---
title: "using 32 bit repos?"
date: 2006-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by arthur_kalm on 2006-01-16
I started to notice package differences between my desktop (64 bit) and my laptop (32 bit). It seems that some packages are completely missing from the repositories available on my desktop (azureus being a major one, and also flashplayer-mozilla). My repository list is exactly the same as that on my laptop, but I assume that when packages are retrieved only the 64-bit packages are looked at. Is there a way to use the 32 bit repositories instead of the 64 bit ones, or should I just install the 32 bit ubuntu?

Thanks in advance.

Here is a my /etc/apt/sources.list

> 
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

#kde 3.5
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main


---

### Post by John Jason Jordan on 2006-01-16
[QUOTE=arthur_kalm]I started to notice package differences between my desktop (64 bit) and my laptop (32 bit). It seems that some packages are completely missing from the repositories available on my desktop (azureus being a major one, and also flashplayer-mozilla). My repository list is exactly the same as that on my laptop, but I assume that when packages are retrieved only the 64-bit packages are looked at. Is there a way to use the 32 bit repositories instead of the 64 bit ones, or should I just install the 32 bit ubuntu?[/QUOTE]
I am far from an expert on such things, but I had the opposite problem. I have Ubuntu only on my laptop, which is AMD-64, so I installed Ubuntu-64 Breezy. Lots of things I wish to run on the laptop are not listed in Synaptic.

Eventually I discovered Chroot and got it installed. This installs a 32-bit environment within 64-bit Ubuntu. From inside this environment I can launch Synaptic32. Anything installed via Synaptic32 is automatically installed in the 32-bit environment. I just have to remember to launch the program with a special command "dchroot -d [program name]."

Perhaps this will help you figure out how to resolve your issue.

---

### Post by RAOF on 2006-01-16
Sadly, the only way to use the 32bit repositories is to use a 32bit system.  Apt is not (yet - it's being worked upon) smart enough to know that 32bit programs can run on x86-64.

There are two ways to get a 32bit system:  you can reinstall with the 32bit version of Ubuntu, or you can set up a chroot, which essentially installs a 32bit version of Ubuntu **inside** your existing Ubuntu install.  If you want to go the chroot route, you could search this forum.  There are any number of posts in here detailing how to do it ;)

---

### Post by arthur_kalm on 2006-01-17
How is the stability of the chroot solution? I will probably go with a 32 bit ubuntu since I have a seperate home directory so there is little to do. But is the chroot solution stable? Thanks.

---

### Post by dabang on 2006-01-17
If you depend on 32bit programs I'd install Ubuntu i386. Some plugins are not available for 64bit, for example Flashplayer or Sun's java plugin for Firefox. And I don't know of Acrobat Reader or Real Player. So the easy way would be using a 32bit OS. If it's for the browser plugins only have a look at this excelent howto:
[https://wiki.ubuntu.com/FirefoxAMD64FlashJava]("https://wiki.ubuntu.com/FirefoxAMD64FlashJava")

---

### Post by St_Iron on 2006-01-17
I have an AMD64 with 32bit Ubuntu 5.10.
When I use the linux, the CPU cooler to be very noisy and fast...
Is it normal?

---

### Post by arthur_kalm on 2006-01-17
> I have an AMD64 with 32bit Ubuntu 5.10.
When I use the linux, the CPU cooler to be very noisy and fast...
Is it normal?

Are you saying that the CPU fan is spinning faster than it normally does? Did it not spin as fast when you used 64 bit Ubuntu or another OS?

---

### Post by St_Iron on 2006-01-17
[QUOTE=arthur_kalm]Are you saying that the CPU fan is spinning faster than it normally does? Did it not spin as fast when you used 64 bit Ubuntu or another OS?[/QUOTE]

Yes, it spins faster. (My english... :))
It is spinning faster than the 64bit version or the M$'s "system"...

---

### Post by St_Iron on 2006-01-17
Maybe the Cool N' Quiet mode...
Isn't it?

---

### Post by John Jason Jordan on 2006-01-17
[QUOTE=arthur_kalm]How is the stability of the chroot solution? I will probably go with a 32 bit ubuntu since I have a seperate home directory so there is little to do. But is the chroot solution stable? Thanks.[/QUOTE]
It is perfectly stable, in my experience. 

Everything on my 64-bit Breezy computer runs in the 64-bit world, except Firefox, RealPlayer and Acrobat Reader 7.0. I had to install those in Chroot to get them to work, but once I did, they work perfectly. Actually, Firefox worked fine in 64-bit also, but I couldn't get the RealPlayer plugin working until I installed it in Chroot.

---

### Post by RAOF on 2006-01-17
[QUOTE=St_Iron]Maybe the Cool N' Quiet mode...
Isn't it?[/QUOTE]
That would be it - in my (brief) experiences with the i386 Ubuntu, it doesn't support the CPU frequency throttling of the amd64 processors.  So the CPU runs hotter and the fan runs more.

---

### Post by St_Iron on 2006-01-20
[QUOTE=RAOF]That would be it - in my (brief) experiences with the i386 Ubuntu, it doesn't support the CPU frequency throttling of the amd64 processors.  So the CPU runs hotter and the fan runs more.[/QUOTE]

Thanks!

---

