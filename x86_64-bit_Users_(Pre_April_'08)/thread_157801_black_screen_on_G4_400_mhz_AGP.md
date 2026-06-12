---
title: "black screen on G4 400 mhz AGP"
date: 2006-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by 2cute4u on 2006-04-09
I have a Mac G4 400 Mhz with a flat panel display connected by DVI.
I tried bookting with the live CD but the screen just went black.  is there a way to get a it to work or live CD that works? I don't have the space to do an install.

Hardware Overview:

  Machine Name:    Power Mac G4 (AGP graphics)
  Machine Model:    PowerMac3,1
  CPU Type:    PowerPC G4  (2.9)
  Number Of CPUs:    1
  CPU Speed:    400 MHz
  L2 Cache (per CPU):    1 MB
  Memory:    1.12 GB
  Bus Speed:    100 MHz
  Boot ROM Version:    4.2.8f1
 
Graphics 
ATY,Rage128Pro:
  Chipset Model:    ATY,Rage128Pro
  Type:    Display
  Bus:    AGP
  Slot:    SLOT-A
  VRAM (Total):    16 MB
  Vendor:    ATI (0x1002)
  Device ID:    0x5046
  Revision ID:    0x0000
  ROM Revision:    113-63001-110
Displays:    
FCT1904Z2:
  Resolution:    1280 x 1024
  Port:    DVI
  Depth:    32-bit Color
  Built-In:    Yes
  Core Image:    Not Supported
  Main Display:    Yes
  Mirror:    Off
  Online:    Yes
  Quartz Extreme:    Not Supported


CD Burner:
QPS CD-R   PX-W8432T:

  Firmware Revision:    1.07
  Interconnect:    ATAPI
  Burn Support:    Yes (Apple Supported)
  Cache:    2048 KB
  Reads DVD:    No
  CD-Write:    -R, -RW
  Burn Underrun Protection CD:    No
  Write Strategies:    CD-TAO, CD-SAO
  Media:    No

---

### Post by linear on 2006-04-10
It's possible that the automated config of your video didn't work. You may be able to fix this after boot, but the Live CD will do the same thing each boot.
 
When you're at the black screen, try this:
 
1. Press ctrl-option-F1 to drop to a shell prompt.
2. Type **sudo dpkg-reconfigure xserver-xorg**. Answer the questions as best you can.
3. When done, type **sudo /etc/init.d/gdm restart** to restart Gnome.
 
You may need to experiment with different screen resolutions.

---

### Post by sarcasticfrench on 2006-04-11
Hmm, I have the same problem on an iMac g4 450 mhz. It starts making the little boot up sound, and it just keeps doing that with a black screen for hours. However, it works just fine on my iBook g3 300 mhz, so I don't think yours is too old or anything. I've actually also tried it on the exact same computer as you minus the cd burner, and the keyboard didn't work at all, at any time, so I was unable to get past the "hit enter to boot" screen. You might want to play around with the options at the boot screen, maybe if you change some of the video options it will work. Also, you might want to try hitting ctrl-alt-f1 to get into the command line, and try typing "startx". That supposedly starts xserver and with it gnome, but on my iMac it said that x server was already running.

---

### Post by 2cute4u on 2006-04-11
[QUOTE=sarcasticfrench]Hmm, I have the same problem on an iMac g3 450 mhz. It starts making the little boot up sound, and it just keeps doing that with a black screen for hours. However, it works just fine on my iBook g3 300 mhz, so I don't think yours is too old or anything. I've actually also tried it on the exact same computer as you minus the cd burner, and the keyboard didn't work at all, at any time, so I was unable to get past the "hit enter to boot" screen. You might want to play around with the options at the boot screen, maybe if you change some of the video options it will work. Also, you might want to try hitting ctrl-alt-f1 to get into the command line, and try typing "startx". That supposedly starts xserver and with it gnome, but on my iMac it said that x server was already running.[/QUOTE]
hitting  ctrl-alt-f1 didn't do anything. I never got a command line. Any idea what options I should try at the boot screen?

---

### Post by linear on 2006-04-11
Did you try ctrl-option-F1 more than once? Sometimes it takes a few tries.

You could try "video=ofonly" at boot, but don't know if it will really do anything.

---

### Post by 2cute4u on 2006-04-12
[QUOTE=linear]Did you try ctrl-option-F1 more than once? Sometimes it takes a few tries.

You could try "video=ofonly" at boot, but don't know if it will really do anything.[/QUOTE]

even after a bunch of tries ctrl-option-F1 didn't do anything.
"video=ofonly" didn't help either

---

### Post by zoombronco on 2006-04-12
i am having a similar problem but with an Apple Display using an Apple Display Connector. if i plug in a VGA monitor, no problem. but my display only shows initial boot information. i can't seem to get the xserver to recognize the ADC... i've searched the forums, but most refer to RADEON cards and ATI utilities. i know there must be a simpler way. i'm using a G4 Cube, and i'd really like to use my studio display.

---

### Post by zoombronco on 2006-04-12
P.S. I am running the keyboard and mouse through the attached USB built into the monitor, so I know the USB hub part of the monitor is working, just not the monitor itself...
and I get "i8042.c: controller not found" just after the the Studio Display turns off (displayed on the VGA monitor). I presume the controller i8042.c mentions is the ADC. Any bells ringing for anyone?

---

### Post by zoombronco on 2006-04-12
[http://www.ubuntuforums.org/showthread.php?t=77200&highlight=ADC](http://www.ubuntuforums.org/showthread.php?t=77200&highlight=ADC)
Another example of this same issue.

---

### Post by 2cute4u on 2006-04-12
[QUOTE=zoombronco][http://www.ubuntuforums.org/showthread.php?t=77200&highlight=ADC](http://www.ubuntuforums.org/showthread.php?t=77200&highlight=ADC)
Another example of this same issue.[/QUOTE]
That guy had a CRT was trying to use ADC and was working with an installed copy.  Any solution to his problem still wouldn't help to boot off a LiveCD on a flat panel connected by DVI

---

### Post by zoombronco on 2006-04-13
Well, my thought is that a problem with the ADC might be similar to the problem with the DVI: an unsupported controller. If we can find out if it's a common cause, we may both find the solution to our problem.

---

### Post by 2cute4u on 2006-04-13
[QUOTE=zoombronco]Well, my thought is that a problem with the ADC might be similar to the problem with the DVI: an unsupported controller. If we can find out if it's a common cause, we may both find the solution to our problem.[/QUOTE]

Someone in [ another thread](http://ubuntuforums.org/showthread.php?t=24043&highlight=G4+blank+screen),  said that they had the same machine and video card as me, but connected to a CRT using VGA,  and it worked, but when they tried to use their LCD  monitor didn't.  So the card works with the LiveCD. It seems the problem is with either using DVI or with using the Planar FCT1904Z2 LCD monitor.

---

