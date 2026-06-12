---
title: "Ubuntu 9.04 - 64 -Hardware installation problems"
date: 2009-11-07
forum: x86 64-bit Users
---

### Post by cyberx0001 on 2009-11-07
[SIZE=3]Ok - I have installed the Ubuntu 9.04 Desktop - 64 bits. The first step
for me is hardware configuration. If it is ok, them the next step is system configuration and after this the step 3 - Softwares installations for my needs.

I stopped in step 1 - Scanner: HP Scanjet 2400 (usb)- not work.
                                    Creative Webcam Live (usb) - not work
                                    Pixelview TV/FM card (pci) (2388x) - not work
                                    Midisport Uno  (usb) - Midi interface - not work

Epson Stylus C67 - Installed C66 driver - No tint manager.

My system: AMD Athlon64 3200+, Asus A8N-SE chipset nvidia nforce4,
Video Card :XFX GeForce 9600GT 512 mb, 2GB ram, Sound onboard, network onboard.

In windows xp, vista , all work ok.

***Questions: Can I install and work with this hardware? How I install it?***
[B]
Note: [/B]Ubuntu 9.10 desktop 64 - not install my adsl internet conexion
            and it work well in 9.04 ??? I dont understand it. 

[/SIZE][SIZE=3]**Linux are cool, but your configuration still hard for not experts. :sad:**[/SIZE]
[SIZE=3]                                    
                                     
[/SIZE]

---

### Post by efflandt on 2009-11-08
I have similar Athlon64 3200+ (the earlier one 2000 MHz w.1024K cache) and some sort of HP proprietary A8N motherboard with on board sound and networking.  Not sure if the later one is any different 2200 MHz w/512K cache.

The only issue I initially noticed in 64-bit 9.04 is that screensavers would crash (so I just use blank screensaver).  That might be related to a problem I had with 64-bit flash plugin (per sticky post at top of this forum), which in 9.04 or 9.10 would vaporize Firefox due to flash advertisements on some sites, but worked fine for flash movies on others.  Apparently my CPU does not have the lahf instruction and the flashplugin-lahf-fix.so mentioned under "illegal instruction" in the sticky flash post resolved that (flash works fine now).

The flashplugin-installer from Synaptic Package Manager did not work properly for me in 64-bit Ubuntu.  It would stop after a commercial and not show news clips.  But it worked fine in 32-bit 9.10 installed on a memory stick.

Everything else I have seems to work in 64-bit Ubuntu 9.04 and 9.10.  Lexmark had a ppd file for my C543dn color laser, so that works in cups.  But it worked in color even from the live install CD using 534dn driver, since either printer does postscript.

You do not provide details about how your DSL is connected (ethernet or USB).  Is PPPoE done on the modem or router, or is it a USB modem and/or are you trying to do PPPoE on your computer?

If you cannot find 64-bit support for your other external hardware, you might see if you can find 32-bit drivers and consider running 32-bit Unbuntu.  Unless you needed 64-bit to support much more RAM there is probably no noticeable speed difference.  And recent 64-bit software may try to use instructions that may not be on earlier chips (like my lahf flash issue).

---

### Post by cyberx0001 on 2009-11-08
hi, my DSL is over ethernet and the Thomson ST 512 v6  modem have bridge configuration. Internet connection work fine in 9.04 destop 64bit. The 9.04 install automatic, after I  put the user and password.

Sound onboard is ok too . AC 97 driver - automatic instalation . In the general, all work  in 9.04 ok, I m testing the system and softwares. My problems is the other hardwares. The DSL problem in 9.10 many peoples have around the world, I thing it is a bug or bad changes in the system. 

Thanks for you sugestion of the 32 bits I go thing about it. The 9.10 I wait more time, for intall it. I want a system for many uses - 3D like seconlife, opensim, max, maya, desktop publishing, midi sequencer  for my yamaha keyboard, movies and prodution and more... more. In windows  all work ok, I like see if in Linux are all I need and if work fine. 

Sorry for my english its bad.

---

### Post by cyberx0001 on 2009-11-14
[SIZE=3]I decided to uninstall everything, install Ubuntu 9.04 32bits.
Solving problems in this version first.

I confess that I am new User of Linux, although not lay in microcontrollers. So I need some time to discover the secrets of this system.

In Ubuntu 9.04 32bit and 64bits,  I had no problems with ADSL

The hardware already solved the problem of interface midi, Midsport Uno, installed as follows:

sudo apt-get install firmware-MIDISport

It worked ok using Rosegarden.


This post are finish - Thanks
[/SIZE]

---

