---
title: "Unable to get &quot;fglrx&quot; drivers to work with Ubuntu 7.04 AMD64"
date: 2007-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by GumbyX on 2007-06-30
I have decided to take the plunge into the 64 bit Ubuntu build and lets just say I am not having the most fun with it. I read about the problems people where having with the AMD64 live CD on ATI cards, so I downloaded the alternative install, which installed fine. I was ready for Ubuntu to crash on me when it first boot, requiring me to install fglrx to get xorg to load,  but to my surprise the default "ati" drivers worked. I logged in, and as usual with any ubuntu install I do on an ATI card, I installed the fglrx drivers (xorg-driver-fglrx) and rebooted. When I did this, I just got a blank screen, and then my monitor went into sleep mode. I reboot and logged into recovery mode to check xorg. The drivers did change to fglrx. I changed it back to ati and I was able to get to the log in screen again. I am at a loss as to why this is happening, so I came here to see if anyone could help me out. 

I am running a AMD Athlon64x2 chip with a ATI Radeon X700 Pro (PCI-E) for a grpahics card. As I said before, for some reason the "ati" driver set by xorg by default worked, but no other driver (fglrx, vesa) gets me anywhere. The only thing I notice that is differnt from the others who have had problems with the AMD64 build and ATI cards is that I am running a PCIE card (most I read about here were AGP cards). I don't think that would be the problem, but you never know.

If there is any more info you guys need, just give me a heads up; I hope someone will be able to help out. I have Ubuntu 6.06 installed on my laptop and I love it (if it wasn't for my college and their network, I would wipe out Windows from it for good!) and I really want to try and get away from Windows on my home PC.

PS For other system specs, the model HP I have is Pavilion a1250n. Hope that helps.

PSS If worse came to worse, and I installed the 32-bit build of Ubuntu 7.04, is there a chance I would run into the same problem? I really want a setup like my laptop (beryl, advent widnow navigator, etc.), so I am willing to drop down to the 32bit build to get it. Thanks Again.

---

### Post by GumbyX on 2007-06-30
Is no one able to help me out? I am sorry, but I am really in a bind here.

Or should I just drop it and go to the 32-bit? I really wanted to try out 64bit but if I am going to run into so many problems, maybe I should just stick with the normal one.....

---

### Post by crjackson on 2007-06-30
I'm pretty new at ubuntu myself but I use SEVERAL computers with ATI / ubuntu both 32bit and 64bit.

What I do is this - if the system boots into the desktop, I download the driver from the ATI/AMD website and install it.  Sometimes I have to repeat the install to get the catalyst control center to work properly.  My systems work great with these drivers.

Hopefully someone with more experience will jump in here and give you the exact information you are looking for.

I almost forgot, I have both PCI-E and intergrated adapters....  PCI-E should have nothing to do with your issue.

---

### Post by praxis22 on 2007-06-30
I doubt it's the ATI drivers, I think it's the ubuntu splash screen, it does the same on mine.

To get around it, boot into recovery mode, then edit **/boot/grub/menu.lst ** remove the word "splash" from every line it appears on in that file and save it out.

Then either reboot, or type **exit** to boot normally.

EDIT:

You may want to type exit first, that way the X will come up and you can use the GUI to edit the file, failing that you'll have to use a command line editor like vi, I can talk you through that if required.

---

### Post by GumbyX on 2007-07-01
Thanks for the heads up guys. One last question: Anyone know if using the DVI port on my graphics card may have something to do with the this problem? I am going to try what each of you said first, but just wanted to see what you thought of it. Thanks agian.

Edit: I downloaded the new driver from the ATI website and used the guide at [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) to install it. I get to the next to last step (just before rebooting) and I get this error:

> gumby@linux-desktop:~/Desktop/ati$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0x00007fffede239fa ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x2af7bdac7396]
aticonfig[0x40a78d]
aticonfig[0x40a6e9]
aticonfig[0x40d963]
aticonfig(XOpenDisplay+0x2b5)[0x402505]
aticonfig(XOpenDisplay+0x139)[0x402389]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2af7bda718e4]
aticonfig(XOpenDisplay+0x5a)[0x4022aa]
======= Memory map: ========
00400000-00423000 r-xp 00000000 08:11 5939241                            /usr/bin/aticonfig
00522000-00529000 rw-p 00022000 08:11 5939241                            /usr/bin/aticonfig
00529000-0054a000 rw-p 00529000 00:00 0                                  [heap]
2af7bcc86000-2af7bcca2000 r-xp 00000000 08:11 18104335                   /lib/ld-2.5.so
2af7bcca2000-2af7bcca6000 rw-p 2af7bcca2000 00:00 0 
2af7bcea1000-2af7bcea3000 rw-p 0001b000 08:11 18104335                   /lib/ld-2.5.so
2af7bcea3000-2af7bcea9000 r-xp 00000000 08:11 5935100                    /usr/lib/libXrandr.so.2.1.0
2af7bcea9000-2af7bd0a9000 ---p 00006000 08:11 5935100                    /usr/lib/libXrandr.so.2.1.0
2af7bd0a9000-2af7bd0aa000 rw-p 00006000 08:11 5935100                    /usr/lib/libXrandr.so.2.1.0
2af7bd0aa000-2af7bd0b3000 r-xp 00000000 08:11 5935003                    /usr/lib/libXrender.so.1.3.0
2af7bd0b3000-2af7bd2b2000 ---p 00009000 08:11 5935003                    /usr/lib/libXrender.so.1.3.0
2af7bd2b2000-2af7bd2b3000 rw-p 00008000 08:11 5935003                    /usr/lib/libXrender.so.1.3.0
2af7bd2b3000-2af7bd2c3000 r-xp 00000000 08:11 5934947                    /usr/lib/libXext.so.6.4.0
2af7bd2c3000-2af7bd4c3000 ---p 00010000 08:11 5934947                    /usr/lib/libXext.so.6.4.0
2af7bd4c3000-2af7bd4c4000 rw-p 00010000 08:11 5934947                    /usr/lib/libXext.so.6.4.0
2af7bd4c4000-2af7bd5ca000 r-xp 00000000 08:11 5934945                    /usr/lib/libX11.so.6.2.0
2af7bd5ca000-2af7bd7ca000 ---p 00106000 08:11 5934945                    /usr/lib/libX11.so.6.2.0
2af7bd7ca000-2af7bd7d1000 rw-p 00106000 08:11 5934945                    /usr/lib/libX11.so.6.2.0
2af7bd7d1000-2af7bd7d2000 rw-p 2af7bd7d1000 00:00 0 
2af7bd7d2000-2af7bd853000 r-xp 00000000 08:11 18104345                   /lib/libm-2.5.so
2af7bd853000-2af7bda52000 ---p 00081000 08:11 18104345                   /lib/libm-2.5.so
2af7bda52000-2af7bda54000 rw-p 00080000 08:11 18104345                   /lib/libm-2.5.so
2af7bda54000-2af7bdb9b000 r-xp 00000000 08:11 18104341                   /lib/libc-2.5.so
2af7bdb9b000-2af7bdd9b000 ---p 00147000 08:11 18104341                   /lib/libc-2.5.so
2af7bdd9b000-2af7bdd9e000 r--p 00147000 08:11 18104341                   /lib/libc-2.5.so
2af7bdd9e000-2af7bdda0000 rw-p 0014a000 08:11 18104341                   /lib/libc-2.5.so
2af7bdda0000-2af7bdda5000 rw-p 2af7bdda0000 00:00 0 
2af7bdda5000-2af7bdda7000 r-xp 00000000 08:11 5934941                    /usr/lib/libXau.so.6.0.0
2af7bdda7000-2af7bdfa6000 ---p 00002000 08:11 5934941                    /usr/lib/libXau.so.6.0.0
2af7bdfa6000-2af7bdfa7000 rw-p 00001000 08:11 5934941                    /usr/lib/libXau.so.6.0.0
2af7bdfa7000-2af7bdfa8000 rw-p 2af7bdfa7000 00:00 0 
2af7bdfa8000-2af7bdfad000 r-xp 00000000 08:11 5934943                    /usr/lib/libXdmcp.so.6.0.0
2af7bdfad000-2af7be1ac000 ---p 00005000 08:11 5934943                    /usr/lib/libXdmcp.so.6.0.0
2af7be1ac000-2af7be1ad000 rw-p 00004000 08:11 5934943                    /usr/lib/libXdmcp.so.6.0.0
2af7be1ad000-2af7be1af000 r-xp 00000000 08:11 18104344                   /lib/libdl-2.5.so
2af7be1af000-2af7be3af000 ---p 00002000 08:11 18104344                   /lib/libdl-2.5.so
2af7be3af000-2af7be3b1000 rw-p 00002000 08:11 18104344                   /lib/libdl-2.5.so
2af7be3b1000-2af7be3b3000 rw-p 2af7be3b1000 00:00 0 
2af7be3b3000-2af7be3c0000 r-xp 00000000 08:11 18104334                   /lib/libgcc_s.so.1
2af7be3c0000-2af7be5c0000 ---p 0000d000 08:11 18104334                   /lib/libgcc_s.so.1
2af7be5c0000-2af7be5c1000 rw-p 0000d000 08:11 18104334                   /lib/libgcc_s.so.1
7fffede0f000-7fffede24000 rw-p 7fffede0f000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
Aborted (core dumped)
gumby@linux-desktop:~/Desktop/ati$ sudo aticonfig --overlay-type=Xv
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

Anyone think they may be able to give me a hand?

---

### Post by praxis22 on 2007-07-01
I'm guessing that would depend on whether the DVI port was the primary port or not. Windows certainly sees them as separate ports, so I'm fairly sure *nix will too.

But no, I doubt it will have any effect on the problem you're having, it'll likely happen whichever port you're actually using if it's what I think it is.

---

### Post by GumbyX on 2007-07-01
> **praxis22 said:**
> I'm guessing that would depend on whether the DVI port was the primary port or not. Windows certainly sees them as separate ports, so I'm fairly sure *nix will too.

But no, I doubt it will have any effect on the problem you're having, it'll likely happen whichever port you're actually using if it's what I think it is.
Thanks for the heads up but I am running into another problem. See my edit above.

Also, will this driver enable me to install Beryl? That is one of the main reasons I am spending this much time on it rather then using the "ati" drivers.

Edit: I just tired to use aticonfig to auto edit my un-editted xorg and it caused the same problem as before. I also noticed it, for some reason, wipes out my xorg. :( Thakfully I had a backup to reload, but I am at a loss as to why this isnt working. :( Anyone got any ideas?

---

### Post by praxis22 on 2007-07-01
Hi,

Ah, that would fairly terminal then.

It looks like the kernel plugin is having a fairly violent disagreement with glibc. Given that that is the core C library without which your whole system is toast I'd remove it and go back to the "ati" driver. It's perfectly possible to run beryl with the "ati" driver, I'm doing so at the moment. 

You'll find instructions on how to re-install the "ati/Radeon" driver here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

This is how I got my system working with Beryl:

[http://ubuntuforums.org/showthread.php?p=1837517#post1837517](http://ubuntuforums.org/showthread.php?p=1837517#post1837517)

Failing that you could try following this and see if it gets you anywhere. I'd still make sure you reinstall the default drivers before you try to re-install the proprietary driver:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Failing that you could try to install the binary drivers via Automatix:

[http://getautomatix.com/](http://getautomatix.com/)

---

### Post by GumbyX on 2007-07-01
Dude, you ROCK!!! I didn't know beryl would run with the "ati" drivers. :-D My laptop has to have "fglrx" in order to do it, so I assumed it had to be the same for my desktop.

Now I got beryl running and I am going to mess around with it. This is so kick @ss. :-D thanks man!! One step closer to getting away from windows1!!

---

### Post by praxis22 on 2007-07-01
If you want it get very silly do the following:

Open Beryl manager,  go to visual effects, enable animations, then click on the "misc settings" tab, and put a tick in the "random animations for all events" box.

Then your tool tips and menus will burst into flames etc. It's stupidly cool!

---

### Post by GumbyX on 2007-07-01
I'll hold off on that for now. ;) But thanks for the info. I am surprised tha AIGLX works so well with my ATI card. I thought it sucked on ATI cards, but I guess you learn something new everyday. I am now the proud user of an 64bit Ubuntu (and XP dual boot for manditory windows stuff) box. Yay!!! :-D

PS The main programs I need XP for is Rhapsody and IE. Rhapsody for my MP3 player (Sansa) and Rhapsody account, and IE for my school's student pages. I am going to WINE IE, but Rhapsody doesn't work in WINE yet. :(

---

