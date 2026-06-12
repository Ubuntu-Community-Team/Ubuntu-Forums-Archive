---
title: "Help on a weird issue."
date: 2008-06-04
forum: x86 64-bit Users
---

### Post by hogwartsnigel on 2008-06-04
Hi guys and thanks in advance. Consider me a newb. I have several machines and have immersed myself in Linux of different flavours, but it was time to settle two machines down and formulate stable boxes.
One was the family PC custom machine using an old Compaq MB 32bit arch and all, fx5700, 500gb mem over 2hdds. 8.04 all installed, Compiz working beautifully on a single Dell lcd monitor. Sweet.

Now the problem started on my other machine is going to low resolution mode no matter what I've tried from clean install. Have filed a bug report and connected to another see 221703. I've tried the downloaded driver, the glx new and using Envy but always returns to vesa Nvidia 7300gt on amd 64 ubuntu ultimate using 8.04 2gb gskill ram, 1905fp dig, and Mitsubishi 2070sb crt, 4 hdd etc

Help anyone on a walkthrough of any more ideas 

Thanks

Nigel see bug 221703

---

### Post by bford16 on 2008-06-04
I saw some stuff on this thread that might help you:
[http://www.uluga.ubuntuforums.org/showthread.php?t=808659&page=2]("http://www.uluga.ubuntuforums.org/showthread.php?t=808659&page=2")

---

### Post by hogwartsnigel on 2008-06-04
Thanks Bford,
I hadn't seen this post but it seems to revolve around the optimisation of the second monitor. Saying that I will try and explore the options for refresh rates etc. in the post when I get home. 
 My bug report entry 
[COLOR="RoyalBlue"]My Box
Li-lian Case 450W PSU, K8ne-Deluxe AMD 64 3400 2.4ghz. 2gb Gskill Ram, 1 x LG dvd/rw 1x LG DVD rom. Nvidia geForce 7300GT 512mb, 1IDE Seagate 3200, 1 IDE Maxtor 250, 2 x SATA (non Raid) 120GB Western Dig. Dell 1905sb (Prim. Digital) and Mitubishi 2070SB (CRT) Attatched Blue tooth dongle, wireless mouse, usb keyboard, 2 USB drives (off), 1 USB Hub.
I did a fresh install on the 3200gb (Replacing an openSUSE 11 beta install) used 8.04 lts uncomplicated install, after finishing updates and rebooting x2 activated restricted driver and rebooted. Low resolution mode splash and option for configure option of two low resolutions inc 800x600 and another. On this occassion I did configure for the Dell LCD and selected driver from driver type selecting geforce 7 series and logged in. vesa was in effect and resolution remained same.
Rebooted and tried non config same result as I expected. (Can't remember my xorg configs but I amended to include monitor and card etc with assistance from forum posts but on reboots kept going to same defult.
Unticked no propritetary drivers and lost one monitor but gained 1280x 1024 resolution on the dell. (this is a familiar look for me when installing previous versions of Ubuntu. But alas didn't help.
Re-installed this time Ubuntu Ultimate to save time on some options later (I know it may compound diagnosing the problem) cloned view of monitors from uncomplicated install at 1280 x 1024 then activating proprietary drivers resulted in the same thing as above. Tried doing a manual install of the latest downloaded from site NVIDIA driver, followed installation formulae and rebooted...same low res. result. Uninstalled all nvidia related files and then tried ENVY...reported success but on reboot same thing. Installed the nvidia configure and ran it and got an xserver not running splash, tried restarting xserver and no improvement.

Forgive the encapsulated view of things I am not on said box at present but at work..planning tonight to commence install after wiping ALL four drives to ensure no ghosting, will use Ubuntu Ultimate again as it gives me a headstart, same problem so I can't imagine any problem generated specific to this install.[/COLOR]

my xorg config file was as follows after reconfiguring on start up

[COLOR="RoyalBlue"]My xorg after trying to configure for my mitsubishi is as follows

"Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "us"
EndSection

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
EndSection

Section "Device"
 Identifier "Configured Video Device"
 Boardname "vesa"
 Busid "PCI:1:0:0"
 Driver "nv"
 Screen 0
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
 Vendorname "Mitsubishi"
 Modelname "Mitsubishi Diamond Pro 2070SB"
 Horizsync 30.0-140.0
 Vertrefresh 50.0-160.0
  modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
  modeline "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline "1856x1392@75" 288.0 1856 1984 2208 2560 1392 1393 1396 1500 -hsync +vsync
  modeline "1920x1440@85" 341.35 1920 2072 2288 2656 1440 1441 1444 1512 -hsync +vsync
  modeline "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline "1920x1440@75" 297.0 1920 2064 2288 2640 1440 1441 1444 1500 -hsync +vsync
  modeline "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
  modeline "2048x1536@85" 388.04 2048 2216 2440 2832 1536 1537 1540 1612 -hsync +vsync
  modeline "2048x1536@75" 340.48 2048 2216 2440 2832 1536 1537 1540 1603 -hsync +vsync
 Gamma 1.0
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "Configured Video Device"
 Monitor "Configured Monitor"
 Defaultdepth 24
 SubSection "Display"
  Depth 24
  Virtual 2048 1536
  Modes "1600x1200@70" "1600x1200@85" "1600x1200@75" "1792x1344@75" "1600x1200@60" "1792x1344@60" "1600x1200@65" "1856x1392@60" "1400x1050@75" "1856x1392@75" "1400x1050@60" "1920x1440@85" "1280x960@75" "1920x1440@60" "1280x1024@60" "1920x1440@75" "1280x1024@85" "2048x1536@60" "1280x960@85" "2048x1536@85" "1280x960@60" "2048x1536@75" "1280x1024@75" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
 EndSubSection
EndSection

Section "ServerLayout"
 Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
 Load "glx"
 Load "GLcore"
 Load "v4l"
EndSection
Section "ServerFlags"
EndSection"[/COLOR]

I isnstalled Nvidia-Settings but on trying to initate that I get an xserver not running message telling me to re-start xserer?
AAAggghhh
Suse 11 here we go if I don't get this sorted

Thanks in advance Nigel

---

