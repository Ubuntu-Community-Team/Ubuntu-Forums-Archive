---
title: "Warning: Xorg Upgrade and FGLRX"
date: 2006-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hygelac on 2006-05-04
There is an upgrade for xorg and the xserver in the repositories.  When I installed it, it ruined my FGLRX (performance was dismal and 'fglrxinfo' would tell me that it was running the inferior Mesa version from the repositories, not the version from the ATI site).  This problem seems to have been remedied by replacing 'libdri.a' (I was using the pre-Breezy version as the Ubuntu FGLRX Tutorial recommends ([http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)), which dpkg seems to have replaced; I just restored the old pre-Breezy version again).  So, I guess this is just a warning to those who are going to upgrade to backup their libdri.a before they do so. [-X  :rolleyes:

---

### Post by matthew on 2006-05-04
Hmm...

Granted, I am not running Kubuntu, but rather Ubuntu. I am also using the 32 bit version.

I did the upgrade and rebooted. This is the output from fglrxinfo on my computer.
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

```In other words, the update worked fine for me.

---

### Post by Hygelac on 2006-05-04
Interesting; your driver sure is working.  Do you suppose it was just some kind of 'routine failure' on my computer (the wrong FGLRX loaded and then I replaced an unchanged library with itself, restarted, and it worked because there was no real problem to begin with)?  I wouldn't really know.  Then again, I thought the libdri.a replacement reccommended in the tutorial only applied to 64bit machines.  Did you have the standard Breezy libdri.a in the first place, or were you using the other (Hoary?) version?

---

### Post by matthew on 2006-05-04
> **Hygelac]Interesting said:**
> That's possible. It will be easier to tell if others begin posting their experiences in this thread. If no one else has the same problem then it must be an unusual occurance on yours. I wouldn't know where to begin to track down the source of the problem.
[quote=Hygelac]I thought the libdri.a replacement reccommended in the tutorial only applied to 64bit machines.  Did you have the standard Breezy libdri.a in the first place, or were you using the other (Hoary?) version?Standard Breezy. You know, it could just be a 64 bit problem...let's see if others comment.

---

### Post by zad on 2006-05-04
think mine is messed up too im getting lines flashing across desktop and when i do fglrxinfo i get

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

my card is ati 9800 pro :S 
unless there is a way of manually telling it to use fglrx it is from the settings

---

### Post by angelillo on 2006-05-04
[QUOTE=matthew]That's possible. It will be easier to tell if others begin posting their experiences in this thread. If no one else has the same problem then it must be an unusual occurance on yours. I wouldn't know where to begin to track down the source of the problem.
Standard Breezy. You know, it could just be a 64 bit problem...let's see if others comment.[/QUOTE]

I am using breezy on AMD64. I confirm that the update went wrong for me, too. My video card model is ATI X700. The output of "fglrxinfo" is:

[FONT="Fixedsys"]libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)[/FONT]

---

### Post by turdomatic on 2006-05-04
*-display
                description: VGA compatible controller
                product: Radeon RV100 QY [Radeon 7000/VE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e0000000-e7ffffff ioport:b000-b0ff iomemory:fd600000-fd60ffff irq:16

above is my ati board - works well and have had no problems. my problem is getting my samsung clp-510 printer working - which doesn't work under anything but xandros and libranet... however that's not for this thread....

---

### Post by towsonu2003 on 2006-05-04
time for you to file away a bug ;)

---

### Post by Hygelac on 2006-05-05
So it really is a problem.  I have never filed a bug report before; is that something just one of us should do, or should we each do it?  For that matter, who does this bug concern (i.e.: ATI, Xorg, Ubuntu, etc...)?
I forgot to mention it earlier, but now that I have seen your posts I will add for the sake of completeness that my card is a Radeon Xpress 200M.

---

### Post by towsonu2003 on 2006-05-05
[QUOTE=Hygelac]So it really is a problem.  I have never filed a bug report before; is that something just one of us should do, or should we each do it?  For that matter, who does this bug concern (i.e.: ATI, Xorg, Ubuntu, etc...)?
I forgot to mention it earlier, but now that I have seen your posts I will add for the sake of completeness that my card is a Radeon Xpress 200M.[/QUOTE]
A bug report is a way for users to let the developers know that something is wrong. 

For example: 
I was trying Dapper (new Ubuntu version) and saw that networking was doing something wrong. So I first searched for a similar bug first, than filed away one. Now the devels are asking me questions to get the bug confirmed. Than, if it is confirmed (i.e. if someone can reproduce it, or if what I am reporting makes some sense), they will start to work on the issue to fix it. 

Go to [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs) and click on "report bug". You'll need a launchpad account (read: register), give as much information in the bug as possible, make sure you follow the bug in case devels need more info, and post the link here so other users with this problem can comment to the bug (in launchpad) and get it confirmed.

Important Note: Filing a bug isn't a way to get help from the devels. If the problem is specific to you, they will not offer help.

---

### Post by Téragone on 2006-05-06
I have the same problem here. The new xorg broke the ATI driver. Using Ubuntu AMD 64, with an ATI 9700 Pro. Driver 8.16.20

Edit : oups. I replace my libdri.a and retstart my X session (CTRL-ALT-BACKSPACE) and all is good now.

---

