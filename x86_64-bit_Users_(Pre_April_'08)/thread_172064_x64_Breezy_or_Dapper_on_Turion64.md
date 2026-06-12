---
title: "x64 Breezy or Dapper on Turion64?"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by mello151 on 2006-05-07
Has anyone be able to install either Breezy or Dapper on the AMD Turion64.  The only x64 Linux distro I've been able to get to work on it so far is Fedora Core 4 and 5.  When I try with Dapper it says something like this:  "kernel panic:  attempting stop" when its loading the kernel.  I can't remember exactly what is says with Breezy but it is something similar.  However, I've gotten the 386 Dapper to work fine.  Any ideas why the x64 doesn't work?  Forgive me if this question has been ask too many times already.  (New to Ubuntu).  Thanx

---

### Post by shintara on 2006-05-08
I was able to get Ubuntu 5.10x64 installed on my Acer 5004WLMi laptop last night with little problem last night using a lot of the defaults, so I know it can be done. Not sure what might be going on with your install.

---

### Post by Aphorism on 2006-05-09
Well it seems to be pretty vague, but here are a few shots into the dark.

[list]
[*] First, try validating your installation media via the md5sum included with Dapper or manually from a command line.
[*] Second, kernel panics will usually point you in a general direction before the bomb.  Does yours?  Can you Google further to locate the issue?
[*] Third, the Turion is just an amd64 architecture chip, and shouldn't really be any problem.  What is your motherboard?  Have you Googled it for Linux kernel issues?  Sometimes it is only one small component of a system that is causing all sorts of problems.
[*] Fourth, if you can get one distro of Linux up, you can generally get any one up with some added help.  I had one system that refused to boot simply because the CD drive was buggery with the media.  Again, check your output.
[*] Fifth, if it is completely random and difficult to trace, check your memory with memtest or something akin to it.
[/list]

Best of luck.

---

### Post by jamesrw on 2006-05-11
I've got Breezy AMD64(Turion) on my Compaq V2000Z. Can't get my card reader to work though. Although I've heard rumor it works in Dapper!?

---

### Post by alastair lewis on 2006-05-11
Breezy AMD64 works out of the box on my Acer Aspire 5002 with a Turion processor. I am currently running the i386 version as i couldn't find 64bit drivers for the Netgear WG511 wireless card. Plan to revisit a 64bit version of Dapper when i move house next month (Wired route access for a while)

---

### Post by bertoldic on 2006-05-11
Hi I've tried 64 bits version of Ubuntu on Asus 2500K (Athlon 64)and they seems to work.However I suggest you to wait until the version that follows Dapper because has been announced a new way to handle 32bit and 64 bit together.So it won't be necessary use only 64bit software.

---

### Post by mello151 on 2006-05-11
Ok, last night I tried Kubuntu Breezy with " live noacpi nolapic"  as  boot options and everything goes fine.  I get to pick languages, hardware, etc.  But as it starts to load everything up it gets to "Checking Battery State......" and goes no further.  I searched the forums and found that the problem may be my graphics card.  I have a ATI Radeon XPress 200M.  So now I'm going to give this a try:  [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver).  I had to do something similar with Fedora Core 4.  I'll let you guys know how it went when I give it a try later tonight.

---

### Post by mello151 on 2006-05-11
Well folks, impatience got the most of me.  (I'm supposed to be studying for my Database exam.  Oh well.)  The link to the tutorial in my previous post worked for me.  Took 10 minutes at the most.  I think that Ubuntu Breezy I tried earlier may have been a bad download.  Isn't Kubuntu the same as Ubuntu with the exception of KDE instead of Gnome?  Anyway, thanx for your help.

---

### Post by masterLoki on 2006-05-20
Well I just woke up this morning and installed 5.04 on my Acer Aspire 5002, all you need is give extra parameter on boot, linux vga=771 and that's all

---

### Post by mello151 on 2006-05-20
I tried that too.  I had to use "noapic nolapic" as boot parameters and then at the command line download the ATI driver "fglrx" to get the X server to start.  I have the Radeon Xpress 200M video card.

---

### Post by Maverick45 on 2006-05-28
Ok. So having read through the basic help files, I figured out I would need to run vga=771 during the boot options. After the first 3 tries for install, I realized I had to also run with the noapic and nolapic options. Now, here's the issue I am having. Not sure if it's based on the Turion64, or if it's just a shitty HP compatibility issue. I am running a laptop. HP Pavillion dv5040us. everything runs smoothly until boot. During boot, the ubuntu logo appears all funky colored. It runs through the module loading, and then instead of the login screen to Gnome, I get a blue screen with vertical white lines running through it. I read a suggested fix action of re-running the xserver config, however this did not work. I am still having the issue. The video card is a ATI X200. If anybody has found a work around for this, I'd appreciate the help. I'm actually starting to look kind of silly to my buddies, who bought Gateway laptops and have had no issues installing any *nix on them.

---

### Post by mello151 on 2006-05-28
Hey Maverick, that's exactly what happened to me also.  I think my laptop is basically the model as yours.  I have the Lance Armstrong Edition.  When I used the vga=771 option at boot the video card wouldn't work.  The only options that I used at boot were noapic and nolapic.  But this is the thing, you only get a command line to work from at first.  You have to download and install the ATI driver to be able to use the Xserver.  Here is the link to the how-to that I used:
[http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)
If you have the 14.1 screen like I do you may have to change your resolution in the xorg.conf to 1280x768. I think I had to.  After you get the driver installed just type 'startx' at the terminal and you should be good to go!

---

