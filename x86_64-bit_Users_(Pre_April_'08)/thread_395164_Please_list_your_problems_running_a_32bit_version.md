---
title: "Please list your problems running a 32bit version"
date: 2007-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Kilz on 2007-03-27
Please read this post before posting in this thread. 
**[COLOR="Red"]This thread isnt for people to report that they have no problems running the 32bit or 64bit version  version. [/COLOR]**
This threads only purpose is to list problems that people have had running the 32bit of Ubuntu on 64bit hardware. It is also not the place to seek help running the 32bit version on 64bit hardware. If you have a problem please make another post.

---

### Post by Jouke74 on 2007-03-28
Ok if you really like:

1/ Most of my calculations take about 30% longer
(with three weeks of calculating time that is quite a difference). 

2/ "Out of memory running application Merlin" Kernel panic, end of process usually at about 1.5 GB. Not there in the 64 bit version :)

---

### Post by Kilz on 2007-03-28
Thanks, I will list mine.

I have an emachine t6524 and the 32bit version does not see my cdrom drive.

---

### Post by Rui Pais on 2007-03-29
Maybe this turn to be an interesting thread...

I have an epson all-in-one (DX5000) that i managed to install on edgy32b with both the closed drivers from [Avasys]("http://www.avasys.jp/english/linux_e/dl_spc.html") as the open source. Although the close source have better quality (on photos) its slower and i decided to stay for the open one. 
But i keep the app for the scanner, iscan. It make scanner work out-of-the-box and interface it's very simple and easy (my wife gets confused with xsane). 

On 64b i don't bothered with the close drivers but i tried to install iscan (it's a alien converted rpm).  It installs but fails to run. 

Another (half) failure its Mathematica5.
I managed to make it run on 64b (just a small change on start script), but it got a refresh page problem and all notebook got illegible when i move the page up and down, make it not much useful for any real work :(.

And thats all i remember now. 
Curiously enough both my failures are closed source apps...

---

### Post by M$LOL on 2007-03-29
I can't get to a GUI when booting from a 32 bit ubuntu CD. (Not that I need or want to).

---

### Post by Kilz on 2007-03-30
bump

---

### Post by Kilz on 2007-04-06
I think this thread would be good for recording all the posts I find with 32bit on 64bit hardware problems, Here is one I found today.

> **nss0000 said:**
> BigR:

My fault. I posted details elsewhere, but ought to have included them in my post here. 

AFAIK it's the new chipsets ( in the ASUS-M2n )  that cause trouble  -- semisupported by UBUNTU.  So upfront I installed a "legacy" NIC and cheapo SB_16 soundcard.  Otherwise, I got NO sound from the onboard soundchip, and NO network from the onboard GB-etherport.

With these fudges,   U_6.06x64 installed and configured automagically from the 'factory' CD ( tho EDGYx32 failed !??).

nss
******

A new one
> **Kxpress said:**
> :cool:I have a 64-bit machine (Thinkpad T61 Intel Centrino T7300 2.0 GHz, 2 GB DDR2 Ram PC5700, 15.4' screen 1680x1055 WXGS+, Nvidia Quadros M140 128MB, 120 GB SATA, CD R/W/DVD-ROM, Intel PRO 3945 Wireles Card) with "three" OSes WinXP Pro 32-bit, Ubuntu 7.04 32-bit, and Unbuntu 7.04 64-bit.

My experience installation for both 32-bit or 64-bit Ubuntu is very simple not much different, however** I noticed for 64-bit Ubuntu the wireless card works consistently while in 32-bit Uncuntu the wireless works off and on ...**

In my machine, the 64-bit Ubuntu's boot time is certainly much faster than Ubuntu 32-bit's. Can I say performance can be recognized here ???? After everything is setlled down, I plan to erase 32-bit partition to regain my disk space for future usage.

I know this is Linux, it is free, I can't expect a simple click as I paid for Window. But if anyone  has succesful installed this type of Graphic Card, please help to lead me step --by-step in making through this process. I am not a software-oriented guy, especcially in Linux..... 

Thank in advance.:)

---

### Post by cmost on 2007-04-06
I cannot use AGP.  amd64_agp module causes random freezes and an inability to initialize the nvidia driver.  I do realize that this is a bug with my particular motherboard (see my specs in my signature for details.)  Further, Windows too has a problem with video unless XP-64 is used.  Disabling AGP altogether (by renaming the amd64_agp module, preventing it from loading) does allow me to load the nvidia driver, but, I cannot use such features as AIGLX (or nvidias implementation of ARGB Visuals) and video performance is horrible.  My research indicated that if I could compile AGPGART as a separate module instead of having it built-in the kernel it may solve the problem, but, that's a laborious proposition.  I can use XGL in the 32 bit OS, however but this has its own problems.  Overall, I find the 32 bit version of Linux noticeably slower.

Since switching to the x86-64 edition of Ubuntu, I've had zero problems!!  I can't wait until Feisty arrives...like fine wine, Ubuntu just keeps getting better and better!

---

