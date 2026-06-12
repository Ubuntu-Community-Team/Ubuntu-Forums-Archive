---
title: "Uninstall Ubuntu from a single-boot PC?"
date: 2008-07-17
forum: x86 64-bit Users
---

### Post by Don Gwinn on 2008-07-17
I've searched and found a lot of good advice on uninstalling Ubuntu from a dual-boot machine, but my problem is different and I haven't seen a thread on it yet.

I built a PC with an Athlon 64 3500+ and installed Ubuntu Studio 8.04--by itself.  I have a legal XP cd and product key, but I had hoped to save those for my old machine, which I want to give to my sister.  I like Ubuntu's stability and the way it's set up, but I can't even begin to comprehend how to get things like video editing software installed--the whole reason I built this rig.  

So now I'd like to either remove Ubuntu in favor of WinXP, or add a WinXP partition and create a dual-boot machine.  From what I've read, I think it would be easier to remove Ubuntu, install WinXP, then install Ubuntu in a partition. 

The problem is, I can't figure out how to get Ubuntu off the machine.  Since there's no WinXP installation, I don't think I can get the Repair Console from the XP CD to make it work.  I can't get the XP CD to run anything in Ubuntu (will Ubuntu not run .exe files?  WTF?) and when I went into the CMOS list and made it boot from CD, it got partway through the XP installation and quit because it said if failed to get some file I've never heard of before.  

Can anyone help me either remove Ubuntu or add WinXP?

---

### Post by Kilz on 2008-07-17
There is a wealth of applications at your fingertips. [Read here.]("http://www.monkeyblog.org/ubuntu/installing/") Avidemux is installable with synaptic, great video editor.


If you have a Windows Xp install disk, it should boot and allow you to install it.

---

### Post by warp99 on 2008-07-17
You can make a second partition and install XP to that partition then recover the Ubuntu boot loader (GRUB) with the following instructions:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Now to make the partition for Windows you can use the Ubuntu LiveCD then use a program called Gparted or you can download the Gparted LiveCD or LiveUSB image instead which is available here:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You can also install Virtualbox or VMWare Server and install XP as a virtual machine. I have the same processor (AMD 3500+) with 2GB of ram and my VMware image of XP with SP2 runs without any issues.

---

### Post by phlembob on 2008-07-18
I hope you have found your answers, but you can boot off the XP cd.  From that point you can place a partition for XP or you can format the entire disk for XP then reinstall Ubuntu.  :guitar:

---

### Post by Don Gwinn on 2008-07-18
Thanks!  I tried booting from the XP CD and it didn't work, but I think it may have found that file it was looking for if I'd been connected to the internet.  I'll try again.

Kilz, thanks for the link.  I keep hearing that there are all these great video options, but I can't even find a way to play .wmv files, and I can't begin to understand how to install software using Ubuntu.  There's this whole process of packages and Synaptic and searches and repositories, and I have no idea what any of it means.

I think I'll ask all that stuff in the Absolute Beginners area.

---

### Post by Yannick Le Saint kyncani on 2008-07-18
> **Don Gwinn said:**
>  I like Ubuntu's stability and the way it's set up, but I can't even begin to comprehend how to get things like video editing software installed--the whole reason I built this rig.

You could install the package ubuntustudio-video, it will install a small selection of video-related software, namely dvgrab, ffmpeg, ffmpeg2theora, kino, openmovieeditor and stopmotion.

---

### Post by Kilz on 2008-07-18
> **Don Gwinn said:**
> 
Kilz, thanks for the link.  I keep hearing that there are all these great video options, but I can't even find a way to play .wmv files, and I can't begin to understand how to install software using Ubuntu.  There's this whole process of packages and Synaptic and searches and repositories, and I have no idea what any of it means.

I think I'll ask all that stuff in the Absolute Beginners area.

Your welcome, that link is a great site to introduce you to everything, take a good look at it because it is probably one of the sites the beginners section will point you to.

---

### Post by cariboo on 2008-07-18
If you boot from you windows CD just let it run until it gets to the partitioning screen and delete the partitons that are already there, then you can create whatever partitions you need to install windows.

If you can get your head around it installing programs in Ubuntu is way easier than doing the same thing in Windows, there is no searching web sites for the program you think you want only to find that it wants to phone home everytime you use it. Never mind that sometimes the program doesn't work the way you expect it to.

The previous posters have posted a lot of links to what you want to do, spend some time reading the guides and get familiar with the processes needed and you won't regret it.

Jim

---

### Post by Don Gwinn on 2008-07-18
OK, so I'm trying to install Avidemux.  I'm having the same problem I had with Thunderbird, Kino, and all the rest.  I went to Synaptic, I did the search, I marked the whatever and I told it to "Apply."  It downloaded six of seven packages, told me it was downloading the seventh, and then asked me to insert the 8.04 disk.  

That was the end of that.  I put the disk in.  I know the machine could see it, because a new window opened up showing all the folders on the disk.  But the message window demanding the disk would not close.  I clicked "OK" about four dozen times to no avail, then finally clicked "cancel."  It asked whether it should proceed without the file it had tried to retrieve, I approved that, and it immediately told me the installation had failed.  

What is going on?

---

### Post by Kilz on 2008-07-18
Its trying to use the old packages from the hardy disk. But they may be to old, or the disk may be bad in that area. In Synaptic, click Settings, then repositories. The repositories window will open , uncheck the boxes in the bottom area where it lists the CD's, click close, then reload in the main toolbar. Then try to install again, this time it will download all the packages.

---

### Post by Don Gwinn on 2008-07-19
THANK YOU!  Hope I did that right.  The only box marked there was "multiverse" but I think that's the only package type I've tried to install.

SUCCESS!  I've been struggling with that for a couple of weeks, and you solved it in ten seconds.  Thank you so much.

Now I have to figure out how to use the program. . . . but I'm sure I'll be back.

---

### Post by Kilz on 2008-07-19
> **Don Gwinn said:**
> THANK YOU!  Hope I did that right.  The only box marked there was "multiverse" but I think that's the only package type I've tried to install.

SUCCESS!  I've been struggling with that for a couple of weeks, and you solved it in ten seconds.  Thank you so much.

Now I have to figure out how to use the program. . . . but I'm sure I'll be back.

Your welcome, we were all new to linux at one time. If you have any more problems just start a post.

---

### Post by blastbar on 2009-06-03
hi is there a way to uninstall ubuntu and leave your system blank?    i don't have any other OS's but i dont want anything on it at the moment?      any help much appreciated =]

---

