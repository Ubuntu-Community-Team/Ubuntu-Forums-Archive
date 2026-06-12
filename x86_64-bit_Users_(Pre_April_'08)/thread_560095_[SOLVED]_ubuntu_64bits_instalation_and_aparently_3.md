---
title: "[SOLVED] ubuntu 64bits instalation and aparently 32bit kernel"
date: 2007-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by bernardobraga on 2007-09-25
Hi. 
I'm new to ubuntu/linux so please, if you can help, please don't assume I know very much (don't skip steps plz)
I've downloaded my ubuntu 64bits from  [http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-amd64.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-amd64.iso)
I asked my friend to try to help me uptade my video card so I went to nvidia website and downloaded "NVIDIA-Linux-x86_64-100.14.19-pkg2.run" here: [http://www.nvidia.com/object/linux_display_amd64_100.14.19.html](http://www.nvidia.com/object/linux_display_amd64_100.14.19.html)

following the steps I got this error:
ERROR: this .run file is intended for the
Linux-x86_64 platform, but you appear to be
running on Linux-x86.  Aborting installation.

I tried uname -a :
 Linux bernardo-desktop 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

My friend told me that means my kernel is 32bits. it seems odd cause I downloaded the ubuntu 64 bits, right?

cat /etc/*release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"

Should I update kernel? Does ubuntu 64 really comes with 32 kernel? Is it something I should have selected on the starting screen?
If the choice is updating kernel, is there a way to make a backup? and how do I update it?

thanks
B.

---

### Post by rsambuca on 2007-09-25
You must have inadvertently downloaded the 32bit iso.  You will have to re-install with the 64bit version.

---

### Post by John.Michael.Kane on 2007-09-25
You downloaded the 32bit iso, As Ubuntu 64bit does not come with a 32bit kernel, and there are no 32bit kernels in the 64bit repo. 

To use 64bit you will have to download the 64bit iso.
[Feisty Fawn 7.04 Desktop Live CD 64bit]("http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-amd64.iso")
[Feisty Fawn 7.04 Alternate install CD 64bit]("http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-amd64.iso")

---

### Post by bernardobraga on 2007-09-25
I HAVE donwloaded the 32bit somehow. Don't know why. I remember checking the box for the 64bit... oh well.
I think i've downloaded some stuff for 64bits. Can I safetly remove them with synaptic or will it remove a bunch of stuff associated to it thus screwing up my configurations? (did something like this once ;~ had to reinstall)

---

### Post by John.Michael.Kane on 2007-09-25
> **bernardobraga said:**
> I HAVE donwloaded the 32bit somehow. Don't know why. I remember checking the box for the 64bit... oh well.
I think i've downloaded some stuff for 64bits. Can I safetly remove them with synaptic or will it remove a bunch of stuff associated to it thus screwing up my configurations? (did something like this once ;~ had to reinstall)

It's my understanding that theres no way currently to move from 32bit to 64bit without doing a clean install. 

Your best off backing up any files of importance to you, and installing clean.

---

### Post by bernardobraga on 2007-09-25
maybe I didn't make myself clear...
After instaling ubuntu, (when I still tought it was 64bit ubuntu) I started synaptic and downloaded gcc 64bits for example...
can I safely remove those 64bits packages I downloaded?

---

### Post by rsambuca on 2007-09-25
If you used Synaptic Package Manager, it will only pull the correct 32bit versions for your system.

---

### Post by bernardobraga on 2007-09-25
yeah but I kinda searched for 64bit libraries and stuff.. Well, I tried removing it and seems I did no harm. Now I learned to check what it's going to uninstall b4 unstalling it ;]
thanks for the help, i'm amazed at the speed ;D
I'll try downloading the 64bit and giving it a go some other day
cya

---

### Post by John.Michael.Kane on 2007-09-25
> **bernardobraga said:**
> maybe I didn't make myself clear...
After instaling ubuntu, (when I still tought it was 64bit ubuntu) I started synaptic and downloaded gcc 64bits for example...
can I safely remove those 64bits packages I downloaded?

Your running a 32bit Os. The programs It installs are not forward compatible with 64bit programs. So the programs you downloaded with synaptic are all 32bit in nature.

To run in 64bit mode you will have to do a clean install after downloading the proper iso from one of the links I posted.

---

### Post by whoop on 2007-09-25
When you do get to installing the nvidia driver you might consider using envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)). It's a really handy application that automates the installation process for the installation of your driver.

---

### Post by Kilz on 2007-09-26
> **bernardobraga said:**
> yeah but I kinda searched for 64bit libraries and stuff.. Well, I tried removing it and seems I did no harm. Now I learned to check what it's going to uninstall b4 unstalling it ;]
thanks for the help, i'm amazed at the speed ;D
I'll try downloading the 64bit and giving it a go some other day
cya

Why put off running the operating system designed for your hardware?

---

