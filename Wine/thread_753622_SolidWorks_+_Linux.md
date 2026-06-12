---
title: "SolidWorks + Linux"
date: 2008-04-12
forum: Wine
---

### Post by [pl]ice on 2008-04-12
Hi guys,
 I wild love to run SolidWorks on Ubuntu, don't wanna run windows etc.
  Any ideas? Can't find any good clues how to do it. 
  Anyone have tried it?
 Thanks :)

---

### Post by ad_267 on 2008-04-12
SolidWorks doesn't run natively on Linux so you're going to have to try using it with wine or use something else like Pro Engineer which has a Linux version.

From this: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=318](http://appdb.winehq.org/objectManager.php?sClass=application&iId=318) it doesn't look like SolidWorks runs very well in wine

---

### Post by maccam94 on 2008-06-10
I'm also interested since I'll be using solidworks in the next year. The version of WINE used to test it on AppDB is pretty old though, it might work better on newer versions.

---

### Post by rkde on 2009-02-07
FYI

I have the latest 2008 and 2009 SW and can confirm there is a way to run them.

I am running kubuntu 8.10 2.5.1 build-126130 not modified.

* instillation under win4lin does work but its very slow and has trouble rendering.
* Wine can install only DWG editor but is unstable, install can't start because it can't find ie7...
* VM player with XP and drivers from VM server runs all solidworks distributions and upgrade patches faster then a native speed XP machine.

I have tried all items on the VM including PDM works and the free DWG editor package. I know its still an install of windows but I only use it for CAD so its fine.

Hope this helps

---

### Post by R2LL2R on 2009-03-05
> **rkde said:**
> FYI

I have the latest 2008 and 2009 SW and can confirm there is a way to run them.

I am running kubuntu 8.10 2.5.1 build-126130 not modified.

* instillation under win4lin does work but its very slow and has trouble rendering.
* Wine can install only DWG editor but is unstable, install can't start because it can't find ie7...
* VM player with XP and drivers from VM server runs all solidworks distributions and upgrade patches faster then a native speed XP machine.

I have tried all items on the VM including PDM works and the free DWG editor package. I know its still an install of windows but I only use it for CAD so its fine.

Hope this helps

Very Helpful, Thanks! :)

Will Post back with a screenshot! :)

---

### Post by dmitriyp13 on 2009-04-02
Has anyone tried out the new VirtualBox (2.1.4 or higher) with SolidWorks?  The reason for the newest version is because VirtualBox now includes 3D accelleration via OpenGL.  However, for me, this leads to refreshing issues within the main screen when a model is loaded.  This problem goes away if I force SolidWorks to use software OpenGL (option within the program).

---

### Post by binbash on 2009-04-02
> **dmitriyp13 said:**
> Has anyone tried out the new VirtualBox (2.1.4 or higher) with SolidWorks?  The reason for the newest version is because VirtualBox now includes 3D accelleration via OpenGL.  However, for me, this leads to refreshing issues within the main screen when a model is loaded.  This problem goes away if I force SolidWorks to use software OpenGL (option within the program).

I will try latest solidworks with newest virtualbox today, i will write down my experience soon : )

---

### Post by poision_heart on 2009-08-26
hi guys..i still not getting solidworks 2008 working on ubuntu9.04..

please guide me

---

### Post by RobotJay on 2009-10-10
I have successfully run SolidWorks on my laptop under Ubuntu Intrepid.  

It was painful and tedious, but in the end, I was able to mount my EXISTING Windows partition under VirtualBox, and run SolidWorks that was installed on that partition.  VirtualBox even has a "seemless" mode, where you see your normal ubuntu desktop, but you also have the Windows start menu bar.  It's quite an amazing piece of free software.

It is worth noting that on the computer I used, SolidWorks ran slowly in XP natively, and excruciatingly slow under Linux. I have a feeling that I would have seen a dramatic increase in performance if I had a multi-core processor, or if I had more than 1GB total system ram (or both.)

This is still a crude and slow way of running SolidWorks under Ubuntu, but it works.

---

### Post by Taras.M.K on 2009-11-30
> **rkde said:**
> 
* VM player with XP and drivers from VM server runs all solidworks distributions and upgrade patches faster then a native speed XP machine.

I have tried all items on the VM including PDM works and the free DWG editor package. I know its still an install of windows but I only use it for CAD so its fine.


Did anyone compare usage of SW in different VMs? Which one suits better (Virtualbox or VMWare, other)?

---

### Post by shadowimmage on 2010-01-05
Hello, I'm starting a class at my university which teaches modeling using solidworks,. My question is if there's any newer developments as far as running solidworks under linux (Ubuntu Karmic).
I haven't done it yet, but I'm thinking it might work if i nstall windows7 on my secondary hard drive for my laptop (ThinkPad T61, ultrabay hdd) and I could use some sort of Virtual Machine (suggestions, preferably free?) To run it that way? I haven't really had much success using Wine for any applications... only Starcraft works for me.... 

One limitation I have is that I have an intel integreated graphics card, and it doesn't really do so well in Ubuntu (or so its been for a while since they started messing with the linux drivers for intel cards....)

Any help would be greatly appreciated!

---

### Post by dmitriyp13 on 2010-01-06
There are two ways you can go about running Solidworks:

1. Install Windows (XP, Vista, and 7 will work) on a seperate partition and dual boot between Ubuntu and Windows.  This method will allow the use of your video card for 3D acceleration in Solidworks.

2. Install Windows in a virtual machine.  I've used VMWare in the past but have liked VirtualBox recently.  I installed a slimmed down version of Windows and only the absolute essential software to keep the virtual machine running efficiently.  Solidworks runs well but you lose the 3D acceleration from your video card.  The usability is still good and I have used this method for the past two years.

I have tried running Solidworks through wine and that turned into a big mess.  In short, dont do it.

---

### Post by robbie d on 2010-01-13
I am trying to install solidworks on xp through virtualbox, I cannot get the installer to actually install it, I select all the options but then the message comes up, the installer was interrupted before it completed. Anyone who has SW running, what extra things did you install to windows to get it to work?

---

### Post by dmitriyp13 on 2010-01-14
I have installed Solidworks in Virtualbox and have not had any kinds of errors during the install process.  It sounds like the installation file for Solidworks could be corrupted.  Do you have another cd you can try installing from?

---

### Post by robbie d on 2010-01-14
The installation disk I have has been used on my other machine and worked ok, I'm thinking it's something to do with my windows installation.

---

### Post by dmitriyp13 on 2010-01-15
The only thing I can think of is to make sure all of the updates have been applied to Windows.

---

### Post by poulsone on 2010-01-26
I am running:
Solidworks 2009 SP 5
WinXP SP 3 virtual machine
VirtualBox 3.1.2
Kubuntu 9.10

It is working very well, with no crashes and good speed.

It works only with 3D acceleration disabled.
It runs much faster with Nested Paging disabled.

---

### Post by Toronaga on 2010-03-20
Hy, I have Ubuntu and I read here that Solidworks don't work very well on Linux.
I have SolidWorks 2007, and I try to install whit wine but is't work
I want to try whit virtual box or vmware fusion.
Wit what it is better??
How I can resolve my problem??

---

### Post by Gemnoc on 2010-03-20
> **Toronaga said:**
> Hy, I have Ubuntu and I read here that Solidworks don't work very well on Linux.
I have SolidWorks 2007, and I try to install whit wine but is't work
I want to try whit virtual box or vmware fusion.
Wit what it is better??
First, did you even care to read the replies here? post #12 from dmitriyp13 should answer that question.

Second, VMWare Fusion is for Mac OS X host systems. It won't run in Ubuntu. For Linux/Windows hosts, you can choose VMWare Workstation, which is sold $189, or VMWare Player, which is free but has limited features.

> How I can resolve my problem??
If you're going to do **serious** work in Solidworks, the only reasonable option is dual-boot. Otherwise you don't use your hardware (CPU speed, memory, graphics) to its full capacity, and it's just plain silly. I worked from home with Solid Edge for 2 years, and as much as it pains me to maintain a Windows OS on my PC, there is no other way if you need to work (and I say **work**, not *play*) with Windows CAD apps.

---

### Post by Toronaga on 2010-03-21
Tx, you confirm to me that I can't work well whit solidWorks in Ubuntu.
I work to another comp whit windows xp, but I want to try also whit ubuntu
So the last chance to run whit VirtualBox
Sory but it is the firs week when I use ubuntu, I liked, but I am "0"
Anyway, Tx

---

### Post by bigseb on 2010-03-21
Its a real pity that SW doesn't work on Linux. Rhino is another one that we use a lot but doesn't run. I have heard from several people that Solidedge DOES work (never actually seen it run on Linux but I've heard  quite often that it does). Solidedge isn't all that different so perhaps y'all should consider switching...

NOTE: before spending money confirm that it does actually run.

---

### Post by Gemnoc on 2010-03-21
> **bigseb said:**
> I have heard from several people that Solidedge DOES work (never actually seen it run on Linux but I've heard  quite often that it does). Solidedge isn't all that different so perhaps y'all should consider switching...

NOTE: before spending money confirm that it does actually run.
I can lay that question to rest real quick: Solid Edge **does not run** on Linux.

We used it at my old workplace, and so I borrowed the install disc for V20 and Solid Edge ST to try it on Ubuntu. Both releases will install, but they won't run.

I'm curious to know where the people you mention found this notion that SE works on Linux. All the WineHQ AppDB [entries for SE]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6023") are rated "garbage". But I would be very interested to know the procedure to make it work if it really does!

Unless they were talking about Solid Edge's big brother, NX. NX (formerly Unigraphics) is the high-end parametric modeling package from Siemens PLM (former UGS), it is a competitor to CATIA and Pro|Engineer. NX4, 5 and 6 can run on Linux 64-bit distros. The latest release, NX7, runs only on Windows for now; I'm not sure if a Linux version will be available.

Pro|Engineer was available on Linux for some time, but the last release was Wildfire 3 back in 2007. PTC judged there was insufficent demand to continue offering it.

---

### Post by bigseb on 2010-03-21
> **Gemnoc said:**
> I can lay that question to rest real quick: Solid Edge **does not run** on Linux.

We used it at my old workplace, and so I borrowed the install disc for V20 and Solid Edge ST to try it on Ubuntu. Both releases will install, but they won't run.

I'm curious to know where the people you mention found this notion that SE works on Linux. All the WineHQ AppDB [entries for SE]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6023") are rated "garbage". But I would be very interested to know the procedure to make it work if it really does!

Unless they were talking about Solid Edge's big brother, NX. NX (formerly Unigraphics) is the high-end parametric modeling package from Siemens PLM (former UGS), it is a competitor to CATIA and Pro|Engineer. NX4, 5 and 6 can run on Linux 64-bit distros. The latest release, NX7, runs only on Windows for now; I'm not sure if a Linux version will be available.

Pro|Engineer was available on Linux for some time, but the last release was Wildfire 3 back in 2007. PTC judged there was insufficent demand to continue offering it.
I could be wrong here but if I remember correctly they were using older versions, like V14 or something. I f I bump into them I'll ask but don't hold your breath... it could be a while.

---

### Post by Gemnoc on 2010-03-21
Interesting... Wine is playing an unending game of catch-up with Windows, the latest Solid Edge and SolidWorks releases being based on .NET 3.5 and other recent MS tools explains why they won't run. It may mean that such an old release as V14 (dating 2003 I think), .NET 2.0 based might work.

---

### Post by kacperpl1 on 2010-04-18
I have big news to all waiting to see Solidworks running on linux. AMD with Supermicro are designing OTOY - open technology that will bring server sided rendering(cloud computing) and guys from Solidworks said they are developing it now so macs and itoys(ipads/ipods/iphones) will be able to connect and use it. Ofcourse it means we will be able to use it on linux aswell. If it means designing on-cloud for every SW2011 license owner we're good to go, worse if they mean they'll sell us rackmount workstations/rendering farms to do the job cause that model is already possible to create with ulteo or other combination of MS TerminalServices with linux clients.

---

### Post by robbie d on 2010-04-28
The problem I had (which also occurred on windows 7) was the lack of C++ from the straight windows install. After installing the pack updates from microsoft, it worked.

---

### Post by yauhen on 2010-05-22
> **robbie d said:**
> I am trying to install solidworks on xp through virtualbox, I cannot get the installer to actually install it, I select all the options but then the message comes up, the installer was interrupted before it completed. Anyone who has SW running, what extra things did you install to windows to get it to work?

+1 
I get the same with SW2010. At first it would get interrupted, but now it just kinda freezes after it goes beyond 50% of installation.
May be I need to disable 3d acceleration or something else?

---

