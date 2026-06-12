---
title: "AMD64 + Hoary + NVidia"
date: 2005-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by ZakZak on 2005-02-06
I installed the AMD64 distro today on my Opteron machine, upgraded it to Hoary, and made sure linux-restricted-modules-2.6.10-2-amd64-generic is installed.  What else do I need to do to get 3D acceleration for my Nvidia card working?

I seem to recall it being just that easy on my P4 laptop, but I'm running Warty there...

Thanks!
-Zak

---

### Post by valadil on 2005-02-06
You have to make sure your XF86Config/xorg.conf is using nvidia isntead of nv or vesa, you need to load the nvidia module, and you need the nvidia-glx package installed.

---

### Post by ZakZak on 2005-02-06
Okay, wow.  That did the trick perfectly - thank you!

Now, what's the "correct" way to make sure the nvidia module gets loaded automatically next time I boot?

THANKS!
-Zak

---

### Post by Tichondrius on 2005-02-07
[QUOTE=ZakZak]Okay, wow.  That did the trick perfectly - thank you!

Now, what's the "correct" way to make sure the nvidia module gets loaded automatically next time I boot?

THANKS!
-Zak[/QUOTE]
 You have to add it to /etc/modules (just add a line with "nvidia" in it). But you could just do "nvidia-glx-config enable" which is a convenience script which changes xorg.conf and /etc/modules, as well as updating the modules dependencies using depmod (which I assume you did as you got it to work at least once, right?).

Btw, i'm having problems with the nvidia-glx driver using hoary-amd64 and a 6600GT. The mouse pointer doesn't show up, even though things do react to the mouse being moved and clicked, it's just that the mouse pointer cannot be seen !! also sometimes lines of text disappear from the screen in firefox and other apps . This happens on a clean install with the nvidia-glx (v6629) package, and although I'm not sure, it seems like a X graphics driver issue.   The strange thing is that the same driver works fine for me on another computer running hoary-amd64 but has a 6800GT video card. Also the same driver works on the same computer running woody-i386 (actually, for woody I used nvidia-kernel-source to create the kernel module, and nvidia-glx from debian unstable, both package v6629 - instead of using the ubuntu repository packages which are only available for hoary). did anyone experience sanything similar ?

---

### Post by AndersAA on 2005-02-07
[QUOTE=Tichondrius]Btw, i'm having problems with the nvidia-glx driver using hoary-amd64 and a 6600GT. The mouse pointer doesn't show up, even though things do react to the mouse being moved and clicked...[/QUOTE]

tried using software cursor?  SWCursor option if I remember correctly.

---

### Post by Tichondrius on 2005-02-08
[QUOTE=AndersAA]tried using software cursor?  SWCursor option if I remember correctly.[/QUOTE]
 Thanks, this helped and now I can see the mouse cursor ! but I still have these random disappearing lines of text, even inside a terminal window. I usually have to scroll the window back and forth to see the text again..... and it's driving me crazy.... 
Any ideas what's causing this crazy bug ? As I mentioned, the same machine running woody-i386 works fine with the same version of the nvidia display drivers v6629 (although the nvidia drivers package used in woody was downloaded from debian, vs the drivers used in hoary were downloaded from Ubuntu's repository). Also, I'm seeing almost no performance boost from using the 64-bit install, so currently I'm sticking to the 32-bit.

---

### Post by AndersAA on 2005-02-08
hmm, dont know, I'd report that as a bug

---

### Post by Tichondrius on 2005-02-09
[QUOTE=AndersAA]hmm, dont know, I'd report that as a bug[/QUOTE]
 Anyone encountered problems wirh AMD64+Nvidia drivers+6600GT  ?? I'm having the same problems on both hoary-amd64 and warty-64 with the nvidia drivers on my 6600GT card. The screen has random corruptions like missing areas, no mouse cursor, etc.   But the same OS and drivers worked in another machine with a 6800GT.  Anyone ?

---

### Post by AndersAA on 2005-02-09
you could try checking [http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14) aswell.

---

### Post by Compwiz on 2005-02-09
[QUOTE=Tichondrius]Anyone encountered problems wirh AMD64+Nvidia drivers+6600GT  ?? I'm having the same problems on both hoary-amd64 and warty-64 with the nvidia drivers on my 6600GT card. The screen has random corruptions like missing areas, no mouse cursor, etc.   But the same OS and drivers worked in another machine with a 6800GT.  Anyone ?[/QUOTE]
ME!!! i can get redhat to work with my 6600GT but not warty ... everything i try fails!! it just sucks ](*,)

---

### Post by Tichondrius on 2005-02-10
[QUOTE=Compwiz]ME!!! i can get redhat to work with my 6600GT but not warty ... everything i try fails!! it just sucks ](*,)[/QUOTE]
 Note that 32-bit warty (i386) works fine with my 6600GT, it's only the 64-bit version which has these strange video problems (on the same machine)......  

Apart from being specific to 64-bit, it might also be related sepcifically to the 6600GT PCI-E,  because the same 64-bit version does works on another machine with 6800GT AGP.  

What are your symptoms ? mine are garbled text in various windows on the screen, as well as a disappearing mouse pointer....

---

### Post by Dylanby on 2005-02-10
It was my understanding that the default NVIDIA packages in Warty (6111) didn't support the 6600, whereas the Hoary packages (6629) did.

---

### Post by Compwiz on 2005-02-13
i tried that vesa thing ... it worked, but now i have to wait for internet on that machine so i can update the drivers to the 3d ones ... im up and running tho, just not online and i have an AGP card. .. not PCIe anyway, the main syptom is the loginscreen flashes all bars but then enters properly, prolly just the drivers not working right

---

### Post by Tichondrius on 2005-02-13
This bug has been [encountered by many other people](http://www.nvnews.net/vbulletin/showthread.php?t=42597&page=1&pp=15)  and solutions to it exist, which I will explain below, but first I'll describe the problem in more detail. The problem occurs only on AMD64 linux distributions, as it is a caused by a bug in X-windows 64-bit versions (both XFree86 and Xorg). This bug causes graphics memory corruptions only for pci-express video cards running using the nvidia 64-bit drivers.  So the main victims of this bug are the 6600/GT cards,  but again - only when running in 64-bit. Also note that the public domain "nv" driver doesn't support the 6600/GT yet, and the "vesa" driver only works with this card in 32-bit mode, so people who are running a 64-bit distribution can't use X-windows !!

The symptoms of the bug are 
(a) A mouse pointer which looks like a large square, or a disappearing mouse pointer.
(b) Text fonts which randomly disappear and/or being displayed garbled in X-terminals and other applications which display text fonts (almost any application).
(c) Text mode terminal (e.g. when pressing ctrl-alt-f1) is completely messed up and illegible.
(d) When X loads, the nvidia logo doesn't display, and instead you see some corrupt image.

As I said, it was diagnosed as a bug in the 64-bit part of the X-windows (xfree86 and xorg) code. A fix does exist and is pretty small, but requires you to recompile X-windows from scratch ([link](http://www.shell.linux.se/xpatrikx/articles/xf86pcibus-bug.html) ). If you don't want to do that, then there is a workaround, which involces adding the following two lines in the "Device" section of the xorg.conf/XFree86-4 configuration file (the section where the "nvidia" driver line is present):

        Option          "SWCursor"
        Option          "NoRenderExtension"

This solves most of the problems, except for the consoles being garbled after you exit from X-windows, but that is really a small problem. Also this workaround doesn't cause performance degradation in games or 3d-apps.

Request to Ubuntu developers: It would be nice if you could incorporate this fix into the haory-amd86 xorg binary package. For example, Gentoo has already done so in the xorg package. I encountered some problems when trying to compile xorg (not related to this change), so I'm still using the workaround above.

---

### Post by MissIbuki on 2005-03-17
I had the same problem actually, with a PowerMac G4 1GHz and the 6600GT. it was quite odd really. But that workaround worked well. Thank you!

---

### Post by c_dog on 2005-03-18
This was mostly a problem with xorg  2.8.0 & 1. It's been fixed in 2.8.2 maybe it's been fixed in the PPC based debs by now also. No need for turning off -inotify during bootup either.

---

### Post by nix on 2005-03-18
I have an A8V-E Deluxe motherboard, amd 64, 6600GT running properly on ubuntu 64 with nvidia.
Initially it wouldn't and I had to add via82cxxx above ide-cd in /etc/modules to make it work (via chipset).  No problems since.
This was documented somewhere in the ubuntu threads (can't find it at the moment) under x86 I think.  Had different modules depending upon system.
May be worth trying.

---

