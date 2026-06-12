---
title: "Why I currently hate Windows and want to completely move over to Ubuntu"
date: 2007-07-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by AegisTalons on 2007-07-25
So here's the background: I reformated my computer recently and installed Feisty x64 and XP64. The Ubuntu install went pretty well. Video, sound, internet worked right out of the box, while for XP64, I had to install 4 different drivers and perform 3 reboots. 

In Ubuntu, I have Firefox 2.0.0.5 x64 working with flash support. I also have the Thunderbird 2.0.0.5 x64 working. Not to mention AWN and Compiz Fusion working. Just took some time and following some tutorials on this lovely forum. 

Windows XP: I cannot for the life of me get Firefox x64 working in windows. I have downloaded multiple versions from different site but I can't get the 64 bit version working and the same goes for Thunderbird. I need XP for SolidWorks, ANSYS, and video games. Also I had to find a new firewall/anti-virus/anti-spyware solution. I was running ZoneAlarm but that was on XP 32, and that worked decent enough. Now I have been searching for different suites that can take care of this problem, while in Ubuntu, I don't have that freaking problem.

Given that Ubuntu has its fair shair of problems, Ubuntu is so much easier to work with, because of the community supporting it. If you don't know, just go to forums, search and if you don't find an answer, post your question. Finding that for Windows is going to be hard.

Here's the biggest question on my mind. What is everyone's experience with WINE and VMware? I need to be able to play video games and run SolidWorks and ANSYS. I know WINE pretty much has the games covered. But it cannot run either SolidWorks or ANSYS. How does VMware work and is it free like WINE? Sorry for the long rant.

---

### Post by dabl on 2007-07-25
VMWare Player is the only way I run Win XP today.  I have a high-end genealogy database app that runs on a MS Visual FoxPro implementation, so I'm stuck with Win XP.  But you don't have to boot it, and deal with all that virus and spyware stuff!  Wine would not run run my app -- I spent a week working with their techs and it just wouldn't quite get the job done 100%.  But VMWare Player 2.0 does a great job -- I'd say try it first and see if it will run your SolidWorks and ANSYS apps.  There is a slight performance penalty, of course, compared to native Windows -- but it's not more than about 10%, as far as I can tell. :)

Yes, VMWare Player is "free is in beer", but there is a EULA for you to accept.

---

### Post by spyros71 on 2007-07-25
Why use vmware? Try VirtualBox instead. I have a complete installation of windows on it. There is no DirectX support neither for vmware nor for Virtual box so no games .... But I have tried varius apps and all is well.
I only keep a small partition with windows on my disk just for the gaming part. I have moved all my activity to Ubuntu and some things well... I still do them on Windows under VirtualBox. I hope that some day I will get rid of windows completely. I think this day is not very far now :):

---

### Post by tszanon on 2007-07-25
I use VMware Server - also free (no fees). No problems at all, but no 3D, which means no 3D games.
You probably will run any Windows application under a virtual machine without any problems, but the best way to be sure is trying.
My limited experience with wine tells me that the applications run faster than in Windows. But don't ask me why! :)

---

### Post by nxt on 2007-07-26
I had the same problems with WinXP x64. Above all that my XP had problems with my motherboard so I had to reactivate them with MS central every other week, as it thought that I have installed new hardware.

No I am running Ubuntu x64 with VMWARE server and I have XP x64 and Vista x64 as guest OS. The 3D acceleration support is only limited, so most games will not run in VMWARE. However this issue is being addressed by the VMWARE team as I heard and they are working on enabling the guest OS to access the graphic card directly (supposedly when running in full screen mode.......myi guess)

 I use my windows for IE testing and primarily for  Photoshop which runs pretty smooth - depends on the amount of memory you give the VM. 

There's also no  AERO for Vista as it lacks the 3D support - but who needs Aero, when you are running Beryl or Compiz Fusion.

You can also seamlessly virtualize with remote desktop. Here is a How to:
[https://help.ubuntu.com/community/SeamlessVirtualization]("https://help.ubuntu.com/community/SeamlessVirtualization")

The idea is, that you boot the virtual machine, but you leave it on the logon screen. Then from ubuntu you call the windows application through a remote desktop service - and the application window appears directly on your ubuntu desktop.

---

### Post by AegisTalons on 2007-07-26
If you say that 3d accerleration support is limited, then I'm going to be having a hard time with VMware running. [SolidWorks]("http://www.solidworks.com"), for those that don't know, is 3d CAD program that relies heavily on 3d graphics and will slow down in an assembly if it does not have correct support. I may be able to get away with VMware using [ANSYS]("http://www.ansys.com"), but ANSYS is also a finicky software (Finite Element Analysis). 

Not to mention, the games that I enjoy running in Windows. Is that everone's experience with VMware regarding 3d support.

---

### Post by tszanon on 2007-07-26
> **AegisTalons said:**
> If you say that 3d accerleration support is limited, then I'm going to be having a hard time with VMware running. [SolidWorks]("http://www.solidworks.com"), for those that don't know, is 3d CAD program that relies heavily on 3d graphics and will slow down in an assembly if it does not have correct support. I may be able to get away with VMware using [ANSYS]("http://www.ansys.com"), but ANSYS is also a finicky software (Finite Element Analysis). 

Not to mention, the games that I enjoy running in Windows. Is that everone's experience with VMware regarding 3d support.
Then maybe you could try VMware Player. I heard some time ago that VMWARE was implementing 3d acceleration in it.
About the games, you have a good chance of running them with wine. I read in these forums that, if a game has a Mac version, then it is likely to run fine under wine.

---

### Post by nxt on 2007-07-26
> **AegisTalons said:**
> If you say that 3d accerleration support is limited, then I'm going to be having a hard time with VMware running. [SolidWorks]("http://www.solidworks.com"), for those that don't know, is 3d CAD program that relies heavily on 3d graphics and will slow down in an assembly if it does not have correct support. I may be able to get away with VMware using [ANSYS]("http://www.ansys.com"), but ANSYS is also a finicky software (Finite Element Analysis). 

Not to mention, the games that I enjoy running in Windows. Is that everone's experience with VMware regarding 3d support.


Basically, you can enable 3D support for VMWARE guest, supporting all the features of DirectX 7 and some of DirectX 8. But I am not sure what are SolidWorks requirements...

Here is a how to:
[http://ubuntuforums.org/showthread.php?t=84344](http://ubuntuforums.org/showthread.php?t=84344)

Regarding gaming - it's probably best to try WINE or CEDEGA

Check out this Wine compatability site
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by AegisTalons on 2007-07-26
Currently, I'm looking into crossover office. I'll tell you guys how that goes.

---

### Post by dmontalvao on 2007-10-03
Is this thread dead? I would like to know if you succeded with Solidworks and Ansys.

I am just a beginner with Ubuntu, and I really want to change to it (currently, I have Feisty 7.04). My 2 main reasons are the following: I have a 4 year laptop and I WILL NOT INSTALL WINDOWS VISTA NOR OFFICE 2007!!!

However, although I have Matlab 2007 and ProE working fine in Ubuntu, I desperatly need Ansys and Labview. None of them runs... I know Ubuntu is not a supported distro for Labview, but for Ansys? I keep getting the message: "Segmentation Fault (Core Dumped)". As far as I can recall, I got something similar with LabView 7.1 in the root terminal.

So, I really need to know if VMWare is able to run Solidworks or Ansys, and if it performs reasonably. If it does, I am sure it will work fine with Labview aswell.  I want to completely remove Windows from my machine, or, at least, stop dual booting. Oh, I am stuborn. I'll keep my main OS Linux. ;)

I hope to hear from you again soon.
Cheers!

---

### Post by dmontalvao on 2007-10-04
OMG!!! I feel so stupid!!!!

After all, everything is ok with Ansys... The problem is I was choosing as "Simulation Environment" on the launcher "Ansys Workbench" instead of "Ansys". Now I can run Ansys Mechanical on Ubuntu Feisty! Woo hoo!

Well, I just posted this here because I think others might be stuck with this aswell.

(I still don't understand why I can't run Ansys Workbench, but, what the heck!)

Cheers!

---

### Post by dotancohen on 2008-03-14
Just to let you know, I am running SolidWorks 2006 in VirtualBox and it runs great. I gave the virtual machine about 1 GB of the 2 GB this system has installed. I see absolutely no performance lag.

---

