---
title: "WOW FPS with Tweaks - What More Can I Do?"
date: 2008-10-17
forum: Wine
---

### Post by Ugeen on 2008-10-17
Hello,

In Wold of Warcraft, I'm getting 5.5-8.0 Frames Per Second (F.P.S.).  I've done the following tweaks, reinstalled from scratch four (4) times, upgraded memory and even switched computers (added memory and video card). I've ran out of ideas of how to get more F.P.S. in W.O.W. :confused:
(additiona thread of mine:  [  nVidia GeForce FX 5200 GPU Enabled?]("http://ubuntuforums.org/showthread.php?t=953198"))

[LIST=1]
[*]What do I need to do to get more FPS in WOW?
[/LIST]
CPU
[LIST]
[*]Dell Dimension 4600
[*]Intel(R) Pentium(R) 4
[*]Dual Processor
[/LIST]
Video Card
[LIST]
[*]PNY Verto nVidia GeForce FX 5200 PCI 256MB DDR ([Google]("http://images.google.com/images?gbv=2&hl=en&q=PNY+Verto+nVidia+GeForce+FX+5200+PCI+256MB+DDR"), [TigerDirect.ca]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=2148789&CatId=319"))
[*]nVidia Driver Version:  173.14.12
[*]Resolution:  1440 x 900
[*]In a Terminal window, I typed:  sudo lshw -C display
[INDENT]
*-display UNCLAIMED
[INDENT]
description: Display controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0
[/INDENT]
*-display
[INDENT]
description: VGA compatible controller
product: NV34 [GeForce FX 5200]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: pm vga_controller bus_master cap_list
configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
[/INDENT]
[/INDENT]
[/LIST]
Operating System
[LIST]
[*]Installed:  xUbuntu
[*]Version:  8.04
[*]Desktop Environment:  Xfce
[*]Release:  Hardy Heron for i386
[/LIST]
System Monitor says
[LIST]
[*]System tab
[LIST]
[*]Ubuntu
[LIST]
[*]Release 8.04 (hardy)
[*]Kernel Linux 2.6.24-21-generic
[/LIST]
[*]Hardware
[LIST]
[*]Memory:  3.0 GiB
[*]Processor 0:  Intel(R) Pentium(R) 4 CPU 2.80GHz
[*]Processor 1:  Intel(R) Pentium(R) 4 CPU 2.80GHz
[/LIST]
[*]System Status
[LIST]
[*]Available disk space:  16.3 GiB
[/LIST]
[/LIST]
[*]Resources tab
[LIST]
[*]Memory and Swap History
[LIST]
[*]Memory:  3.0 GiB
[*]Swap:  5 GiB
[/LIST]
[/LIST]
[/LIST]
EnvyNG
[LIST]
[*]NVIDIA:  Install the NVIDIA driver (Automatic Hardware Detection)
[/LIST]
[Speed Test]("http://www.speedtest.net/")
[LIST]
[*]Download (Average):  7689 kb/s
[*]Upload (Average):  509 kb/s
[/LIST]
FireStarter
[LIST]
[*]Policy tab
[LIST]
[*]Allow Service
[LIST]
[*]Ports
[LIST]
[*]6122 -- Anyone -- Selected
[*]3724 -- Anyone -- Selected
[*]6881-6999 -- Anyone -- Selected
[/LIST]
[/LIST]
[/LIST]
[/LIST]
Rendering
[LIST]
[*]In a Terminal window, I typed:  glxinfo | grep rendering
[INDENT]
direct rendering:  Yes
[/INDENT]
[/LIST]
Wine
[LIST]
[*]Version:  1.1.6
[LIST]
[*]Wine Configuration
[LIST]
[*]Applications tab
[LIST]
[*]Windows Version:  Windows XP
[/LIST]
[*]Graphics tab
[LIST]
[*]Window Settings
[LIST]
[*]Allow DirectX apps to stop the mouse leaving their window -- Unticked
[*]Allow the window manager to decorate the windows -- Ticked
[*]Allow the window manager to control the windows -- Ticked
[*]Emulate a virtual desktop -- Unticked
[/LIST]
[*]Direct3D
[LIST]
[*]Vertex Shader Support option:  Hardware
[*]Allow Pixel Shader (if supported by hardware) -- Ticked
[/LIST]
[*]Screen Resolution
[LIST]
[*]dpi:  96
[/LIST]
[/LIST]
[/LIST]
[LIST]
[*]Audio tab
[LIST]
[*]ALSA Driver -- Ticked
[/LIST]
[/LIST]
[/LIST]
[*]RegEdit
[LIST]
[*]HKEY_CURRENT_USER \ Software \ Wine \
[LIST]
[*]Key:  Direct3D
[LIST]
[*]String:  DirectDrawRenderer
[LIST]
[*]Value Data:  opengl
[/LIST]
[/LIST]
[/LIST]
[LIST]
[*]Key:  OpenGL
[LIST]
[*]String:  DisabledExtensions
[LIST]
[*]Value Data:  GL_ARB_vertex_buffer_object
[/LIST]
[/LIST]
[/LIST]
[/LIST]
[/LIST]
.wine \ drive_c \ Program Files \ World of Warcraft \ WTF \ Config.wtf
[LIST]
[*]SET ffxDeath "0"
[*]SET ffxGlow "0"
[*]SET SoundOutputSystem "1"
[*]SET SoundBufferSize "150"
[/LIST]
.wine \ drive_c \ windows \ system32 \
[LIST]
[*]msvcp60.dll
[*]mfc42.dll
[*]riched20.dll
[*]riched32.dll
[/LIST]
World of Warcraft (WOW)
[LIST]
[*]Blizzard Downloader
[LIST]
[*]Packets download with no problems at this time.
[/LIST]
[*]Resolution
[LIST]
[*]Resolution:  800x600
[*]Vertical Sync:  Unticked
[*]Hardware Cursor:  Ticked
[*]Reduced Input Lag:  Ticked
[*]Windowed Mode:  Ticked
[*]Maximized:  Unticked
[*]Disable Resize:  Unticked
[/LIST]
[*]Effects
[LIST]
[*]Video Quality:  Low
[*]Shaders
[LIST]
[*]Specular Lighting:  Unticked
[*]Dealth Effect:  Unticked
[*]Full-Screen Glow Effect:  Unticked
[/LIST]
[/LIST]
[*]Chat Window
(i.e. the 0 are zeros)
[LIST]
[*]I typed:  /console maxfps 100
[*]I typed:  /console maxfpsbk 3
[*]I typed:  /console groundEffectDensity 0
[*]I typed:  /console groundEffectDist 0
[*]I typed:  /console detailDoodadAlpha 1
[*]I typed:  /console horizonfarclip 1
[*]I typed:  /console farclip 1
[*]I typed:  /console characterAmbient 0
[*]I typed:  /console smallcull 0
[*]I typed:  /console skycloudlod 1
[/LIST]
[*]Teldrassil \ Dolanaar
[LIST]
[*]Location:  Inside Inn
[*]Looking at:  Keldas (Pet Trainer)
[LIST]
[*]-d3d
[LIST]
[*]FPS:  5.5
[*]Mouse:  Faster than opengl
[/LIST]
[*]-opengl
[LIST]
[*]FPS:  6.0-8.0
[*]Mouse:  About the same or slightly slower than d3d
[/LIST]
[/LIST]
[/LIST]
[/LIST]
Thank you in advance for your help.
Sincerely,
--Ugeen

---

### Post by Delvien on 2008-10-19
Get a better video card.

---

### Post by Ugeen on 2008-10-19
> **Delvien said:**
> Get a better video card.

My graphics card does very well with Firefox, Flash 10, [YouTube]("http://www.youtube.com/"), [Hulu]("http://www.hulu.com/"), etc. with one exception:  World of Warcraft.

[LIST=1]
[*]Could it really be that my graphics card is obsolete?
[/LIST]
My Graphics Card:  nVidia GeForce FX 5200
(additiona thread of mine:  [  nVidia GeForce FX 5200 GPU Enabled?]("http://ubuntuforums.org/showthread.php?t=953198"))

--Ugeen

---

### Post by lakersforce on 2008-10-20
> **Ugeen said:**
> 
[LIST=1]
[*]Could it really be that my graphics card is obsolete?
[/LIST]
My Graphics Card:  nVidia GeForce FX 5200


YES!

I would recommend at least the 6xxx series as a absolute minimum for running WoW on linux.

---

### Post by sethvath on 2008-10-20
Ask a few more people with similar video cards, I have an old geforcego card on my laptop and I still get 32-45 fps on it. 5-8 fps is really low, are you referring to normal game play or 5-8 fps in a full 25 man raid instance? 

Shattrath gives me 19-25 fps usually, depending on the number of people online.

---

### Post by Colro on 2008-10-20
> **Ugeen said:**
> My graphics card does very well with Firefox, Flash 10, [YouTube]("http://www.youtube.com/"), [Hulu]("http://www.hulu.com/"), etc. with one exception:  World of Warcraft.

Entirely different league of comparisons there. That card's got to go.

---

### Post by Espryon on 2008-10-20
The highest vid card with nvidia is a 8900 i think you need to upgrade then that will fix your problem:lolflag:.

---

### Post by Ugeen on 2008-10-20
> **sethvath said:**
> Ask a few more people with similar video cards, I have an old geforcego card on my laptop and I still get 32-45 fps on it. 5-8 fps is really low, are you referring to normal game play or 5-8 fps in a full 25 man raid instance? 

Shattrath gives me 19-25 fps usually, depending on the number of people online.

Hello Sethvath,

I'm not in a Raid.  I've been testing in the following noobie city.

Teldrassil \ Dolanaar
[LIST]
[*]Location:  Inside Inn
[*]Looking at:  Keldas (Pet Trainer)
[LIST]
[*]-d3d
[LIST]
[*]FPS:  5.5
[*]Mouse:  Faster than opengl
[/LIST]
[*]-opengl
[LIST]
[*]FPS:  6.0-8.0
[*]Mouse:  About the same or slightly slower than d3d
[/LIST]
[/LIST]
[/LIST]
Thank you again for your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-20
> **Ugeen said:**
> FireStarter
[LIST]
[*]Policy tab
[LIST]
[*]Allow Service
[LIST]
[*]Ports
[LIST]
[*]6122 -- Anyone -- Selected
[*]3724 -- Anyone -- Selected
[*]6881-6999 -- Anyone -- Selected
[/LIST]
[/LIST]
[/LIST]
[/LIST]


Hello,
[LIST=1]
Could it be my FireStarter settings\open ports?
[/LIST]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-20
> **Ugeen said:**
> Video Card
[LIST]
[*]nVidia GeForce FX 5200
[*]nVidia Driver Version:  173.14.12
[*]Resolution:  1440 x 900
[*]In a Terminal window, I typed:  sudo lshw -C display
[INDENT]
*-display UNCLAIMED
[INDENT]
description: Display controller
product: 82865G Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: pm cap_list
configuration: latency=0
[/INDENT]
*-display
[INDENT]
description: VGA compatible controller
product: NV34 [GeForce FX 5200]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a1
width: 32 bits
clock: 66MHz
capabilities: pm vga_controller bus_master cap_list
configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
[/INDENT]
[/INDENT]
[/LIST]


Hello,
[LIST=1]
[*]Could it be that my graphics card is in a certain slot?
[/LIST]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Thelasko on 2008-10-20
I hear running [Wine in it's own X-server]("http://ubuntuforums.org/showpost.php?p=3908174&postcount=2") drastically increases frame rates.  I've never been able to get it to work.

---

### Post by Ugeen on 2008-10-20
Hello,
[LIST=1]
[*]Could the lack of FPS be from ticking or unticking the DirectX setting within Wine?
[LIST]
[*]Tick?
[/LIST]
or
[LIST]
[*]Untick?
[/LIST]
FYI:  Ticked or Unticked, had no effect on my FPS. -- Mon., Oct. 20, 2008
[/LIST]
Microsoft DirectX
[LIST]
[*]From what I've seen through other websites, Wine handles:  DirectX. -- Tue., Oct. 21, 2008
FYI:  Microsoft DirectX is available but it is _not_ recommanded (i.e. don't install it). -- Tue., Oct. 21, 2008
[LIST]
[*][Wine-Reviews]("http://wine-reviews.net/"):  [http://wine-reviews.net/microsoft/directx-10-for-xp-in-wine.html]("http://wine-reviews.net/microsoft/directx-10-for-xp-in-wine.html") -- Tue., Oct. 21, 2008
[/LIST]
[/LIST]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-20
Hello,
[LIST=1]
[*]Could the lack of FPS be from using the Config file instead of the **x**Config file?
[LIST]
[*]Config file?
[/LIST]
or
[LIST]
[*]xConfig file?
[LIST=a]
[*]How would I install the xConfig, if need?
[/LIST]
[/LIST]
[/LIST]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-20
Hello,
[LIST=1]
[*]Could the lack of FPS be from enabling or disabling the Graphics Processing Unit (GPU)?
(additional thread of mine:  [nVidia GeForce FX 5200 GPU Enabled?]("http://ubuntuforums.org/showthread.php?t=953198"))
[LIST]
[*]Enable GPU?
[/LIST]
or
[LIST]
[*]Disable GPU?
[/LIST]
[/LIST]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by sethvath on 2008-10-21
Before you upgrade your video card, give thelasko's suggestion a try. I'm curious whether it helps the fps rate by running in a seperate x-server.

---

### Post by Ugeen on 2008-10-21
> **sethvath said:**
> 
Before you upgrade your video card


Hello sethvath,

I'm debating on upgrading my graphics card, nVidia GeForce FX 5200 PCI, because my computer does not have a PCI slot.
(i.e. my Peripheral Component Interconnect (PCI) graphics card is in an Accelerated Graphics Port (AGP) slot.)

I might go with a whole new computer but I'm still thinking about.

[LIST]
My Options
[LIST]
[*]New Computer with PCI slots
[LIST]
[*]New Graphics Card
[/LIST]
[/LIST]
or
[LIST]
New Graphics Card for an AGP slot
[/LIST]
[/LIST]
Thank you again for all your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-21
> **Thelasko said:**
> 
I hear running [Wine in it's own X-server]("http://ubuntuforums.org/showpost.php?p=3908174&postcount=2") drastically increases frame rates.  I've never been able to get it to work.

> **sethvath said:**
> 
give thelasko's suggestion a try. I'm curious whether it helps the fps rate by running in a seperate x-server.


Hello Thelasko and sethvath,

After some tweaking, I got the [Wine in it's own X-server]("http://ubuntuforums.org/showpost.php?p=3908174&postcount=2") to work and yes, it did improve my FPS.
(i.e. I went from 2.5 FPS to 4.5 FPS. :))

My concern now is that there was an administrator message that said that the WOW team is working on fixing a latency problem.  Odd, right, since my FPS didn't change.  And even though it was just a little, that tweak improved my FPS.

[LIST=1]
[*]Is there something wrong with my Wine (e.g. a setting)?


[*]How does Wine connect to the internet?
[/LIST]

Running the following commands in WOW's chat window took my 4.5 FPS to 6.0 FPS. :)
(i.e. do in order)
[INDENT]
/console maxfps 100
/console maxfpsbk 3
[/INDENT]


In WOW, I created a macro and added the following code to it.  My 6.0 FPS decreased to 0.7 FPS.
[INDENT]
/console groundEffectDensity 256 
/console groundEffectDist 140
/console detailDoodadAlpha 100
/console horizonfarclip 2112
/console farclip 777 
/console smallcull 0
/console characterAmbient 0
/console skycloudlod 3
[/INDENT]


In WOW, I created a macro and added the following code to it.  My 6.0 FPS decreased to 4.3 FPS.
[INDENT]
/console groundEffectDensity 16
/console groundEffectDist 70
/console detailDoodadAlpha 1
/console horizonfarclip 1305
/console farclip 477 
/console smallcull 0.040000
/console characterAmbient 1
/console skycloudlod 1
[/INDENT]


In WOW, I created a macro and added the following code to it.  My 6.0 FPS increased to 7.3 FPS.
[INDENT]
/console groundEffectDensity 0
/console groundEffectDist 0
/console detailDoodadAlpha 1
/console horizonfarclip 1
/console farclip 1
/console characterAmbient 0
/console smallcull 0
/console skycloudlod 1
[/INDENT]


Thank you again for all your help.
Sincerely,
--Ugeen

---

### Post by sethvath on 2008-10-21
From what I gather there is not much data being sent to blizzard's servers while you play the game. 14kb/s tops for my case, set your firewall to log packets if you want to find out. 

FPS is only determined by your hardware specs and has nothing to do with your broadband speed. Are your wow game settings set to the lowest already or at the default values?

There is a howto for wow on wine on this forum. Attempt all the tweaks in that tutorial and see whether that works for you. If not its probably time to replace that video card. 

I would expect the fps to increase if you play wow with its own x-server but did the ram usage increase too? 

The wow administrator mail might be due to the new patch 3.02 applied last week. I dont play the game anymore so I cant tell whether fps has generally improved or deteriorated. Ask someone in game - your friend or guild mate.

---

### Post by Ugeen on 2008-10-21
> **sethvath said:**
> 
From what I gather there is not much data being sent to blizzard's servers while you play the game. 14kb/s tops for my case, set your firewall to log packets if you want to find out.

Hello sethvath,

Firestarter says:
[LIST]
[*]1.6 MB Received
[*]0.4 MB Sent
[*]0.2 KB Activity -- Lowest
[*]1.0 KB Activity -- Highest
[/LIST]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-21
> **sethvath said:**
> 
FPS is only determined by your hardware specs and has nothing to do with your broadband speed. Are your wow game settings set to the lowest already or at the default values?

Hello sethvath,

My WOW game settings are set to the lowest.  I continue to lower them as I find the tweaks in my quest to play WOW at a decent speed, which could be right around the corner.  I'm almost at stick figures.

Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-22
> **sethvath said:**
> 
I would expect the fps to increase if you play wow with its own x-server but did the ram usage increase too? 

Hello sethvath,

I got the following from doing an Ctrl+Alt+2, typed:  top

Using my desktop shortcut
[LIST]
[*]Mem Used:  809,000 KB
[*]FPS: 7.0
[/LIST]
X-Server in Ctrl+Alt+1
[LIST]
[*]Mem Used:  885,000 KB
[*]FPS: 5.5
(I'm not sure why the FPS dropped.  It was better than the desktop shortcut.)
[/LIST]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Eviljim on 2008-10-22
The FX or 5xxx series cards are getting on now. Blizz now recommends 74xx cards or higher when using XP SP3/MAC OS, so it could be taken to be similar for linux?

However, before ditching the g/card have you tried the latest nvidia driver

[http://www.nvidia.co.uk/object/linux_display_ia32_177.80_uk.html]("http://www.nvidia.co.uk/object/linux_display_ia32_177.80_uk.html")

and turned everything down to low?

---

### Post by Ugeen on 2008-10-22
> **Eviljim said:**
> 
The FX or 5xxx series cards are getting on now. Blizz now recommends 74xx cards or higher when using XP SP3/MAC OS, so it could be taken to be similar for linux?

However, before ditching the g/card have you tried the latest nvidia driver

[http://www.nvidia.co.uk/object/linux_display_ia32_177.80_uk.html]("http://www.nvidia.co.uk/object/linux_display_ia32_177.80_uk.html")

and turned everything down to low?

Hello Eviljim,

When you say, "turned everything down to low?," if you're referring to my settings within:
[LIST=1]
[*]nVidia -- How would I do so?
(FYI:  Currently, it's at its default settings.)


[*]Wine -- How would I do so?
(FYI:  Currently, it's at its deafult settings.)


[*]World of Warcraft -- Yes, and more every day.
(FYI:  Too many to list, again.)
[/LIST]

I'm using EnvyNG to automatically update my nVidia GeForce FX 5000 PCI graphics driver.  I'm not sure why EnvyNG hasn't already installed the 177.80 driver.  The install had a problem and it said to look at the end of this file.
> 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Oct 22 19:27:24 2008
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: The NVIDIA GeForce FX 5200 GPU installed in this system is supported
         through the NVIDIA 173.14.xx legacy Linux graphics drivers.  Please
         visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more information. 
         The 177.80 NVIDIA Linux graphics driver will ignore this GPU.
WARNING: You do not appear to have an NVIDIA GPU supported by the 177.80 NVIDIA
         Linux graphics driver installed in this system.  For further details,
         please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README
         available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
-> License accepted.
-> Installing NVIDIA driver version 177.80.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-21-generic/build'
-> Kernel output path: '/lib/modules/2.6.24-21-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-21-gener
   ic/build SYSOUT=/lib/modules/2.6.24-21-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-21-generic/build SUBDIRS
   =/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_versio
   ns ; rm -f /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_vers
   ions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-p
   kg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nv.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  
   -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototyp
   es -Wno-trigraphs -fno-strict-aliasing
    -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -m
   regparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtu
   ne=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mac
   h-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-
   statement -Wno-pointer-sign   -I/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1
   /usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscrip
   ts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare
   -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\
   "177.80\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD
   _BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/
   selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz6298
   /NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nv-vm.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL
   __  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-func
   tion-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumu
   late-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g 
   -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tm
   p/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wall -Wimplicit -Wretu
   rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -W
   no-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBUG -U_DEBUG -DNDEB
   UG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6298/NVIDIA-Linux-x86-17
   7.80-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pk
   g1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.os-agp
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-
   struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffre
   estanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit
   -frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-p
   ointer-sign   -I/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wal
   l -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses
   -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -
   Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBU
   G -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD
   _STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6298/N
   VIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz6298/NVIDIA-
   Linux-x86-177.80-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.os-int
   erface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D_
   _KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retu
   rn -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -
   maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-poin
   ter -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign
     -I/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D
   __KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBUG -U_D
   EBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(o
   s_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6298/N
   VIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz6298/N
   VIDIA-Linux-x86-177.80-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.os-reg
   istry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__
   KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retur
   n -mpreferred
   -stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-ou
   tgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-s
   tack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tmp/self
   gz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -
   DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBUG -U_DEBUG -DNDEBUG  -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"K
   BUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6298/NVIDIA-Linux-x86-177
   .80-pkg1/usr/src/nv/.tmp_os-registry.o /tmp/selfgz6298/NVIDIA-Linux-x86-177.
   80-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nv-i2c
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccum
   ulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g
    -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/t
   mp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wall -Wimplicit -Wret
   urn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -
   Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBUG -U_DEBUG -
   DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz6298/NVIDIA-Linux-
   x86-177.80-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz6298/NVIDIA-Linux-x86-17
   7.80-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nvacpi
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=gener
   ic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-defaul
   t -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statemen
   t -Wno-pointer-sign   -I/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src
   /nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpar
   entheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80
   \" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENA
   ME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/sel
   fgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz629
   8/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     ld -m elf_i386 -m elf_i386   -r -o /tmp/selfgz6298/NVIDIA-Linux-x86-177.80
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/s
   rc/nv/nv-kernel.o /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/nv
   .o /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/os-agp.o /tmp/selfgz6298/NVID
   IA-Linux-x86-177.80-pkg1/usr/src/nv/os-interface.o /tmp/selfgz6298/NVIDIA-Li
   nux-x86-177.80-pkg1/usr/src/nv/os-registry.o /tmp/selfgz6298/NVIDIA-Linux-x8
   6-177.80-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pk
   g1/usr/src/nv/nvacpi.o
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.24-21-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-21-generic/Modu
   le.symvers -I /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/Module
   .symvers -o /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/Module.s
   ymvers -w -s
   WARNING: could not find /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src
   /nv/.nv-kernel.o.cmd for /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/sr
   c/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nvidia
   .mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__K
   ERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -mac
   cumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer
   -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_M
   ODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /tmp/selfgz6298/NVIDIA-Linux-x86-1
   77.80-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-p
   kg1/usr/src/nv/nvi
   dia.mod.c
     ld -m elf_i386 -r -m elf_i386  --build-id -o /tmp/selfgz6298/NVIDIA-Linux-
   x86-177.80-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz6298/NVIDIA-Linux-x86-177.80
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz6298/NVIDIA-Linux-x86-177.80-pkg1/usr/s
   rc/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   53.280653] NET: Registered protocol family 31
   [   53.280661] Bluetooth: HCI device and connection manager initialized
   [   53.280668] Bluetooth: HCI socket layer initialized
   [   53.331028] Bluetooth: L2CAP ver 2.9
   [   53.331037] Bluetooth: L2CAP socket layer initialized
   [   53.400037] input: b43-phy0 as /devices/virtual/input/input6
   [   53.420393] Bluetooth: RFCOMM socket layer initialized
   [   53.420414] Bluetooth: RFCOMM TTY layer initialized
   [   53.420419] Bluetooth: RFCOMM ver 1.8
   [   53.560710] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or
   load failed.
   [   53.560882] b43-phy0 ERROR: You must go to
   [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download
   the correct firmware (version 4).
   [   56.208404] input: b43-phy0 as /devices/virtual/input/input7
   [   56.289633] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or
   load failed.
   [   56.289647] b43-phy0 ERROR: You must go to
   [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download
   the correct firmware (version 4).
   [   57.844860] NET: Registered protocol family 17
   [   61.474955] NET: Registered protocol family 10
   [   61.475654] lo: Disabled Privacy Extensions
   [   71.953993] eth0: no IPv6 routers present
   [  276.058497] nvidia: module license 'NVIDIA' taints kernel.
   [  276.064959] NVRM: The NVIDIA GeForce FX 5200 GPU installed in this system
   is
   [  276.064964] NVRM:  supported through the NVIDIA 173.14.xx Legacy drivers.
   Please
   [  276.064967] NVRM:  visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more
   [  276.064969] NVRM:  information.  The 177.80 NVIDIA driver will ignore
   [  276.064971] NVRM:  this GPU.  Continuing probe...
   [  276.066643] NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Valok on 2008-10-22
I used to play WoW with a computer similar to the one you have.  And the long and the short of it is that those system specs can only take you so far in terms of FPS.  If you really want to see and FPS boost I would suggest getting more RAM followed by a graphics card.  They are both pretty cheep nowadays.

---

### Post by UltimaDude on 2008-10-22
What's your performance on XP? I know my old 6200 TurboCache ran WoW really badly, and I'm now on my 9600GT(check specs) it runs worse than Windows but I can get a steady FPS around 60 on high settings.

---

### Post by Ugeen on 2008-10-22
> **Valok said:**
> 
I used to play WoW with a computer similar to the one you have.  And the long and the short of it is that those system specs can only take you so far in terms of FPS.  If you really want to see and FPS boost I would suggest getting more RAM followed by a graphics card.  They are both pretty cheep nowadays.

Hello Valok,

My RAM is at 3 GiBs.

My graphics card seems to be the culprit.
> **Ugeen said:**
> 
Hello sethvath,

I'm debating on upgrading my graphics card, nVidia GeForce FX 5200 PCI, because my computer does not have a PCI slot.
(i.e. my Peripheral Component Interconnect (PCI) graphics card is in an Accelerated Graphics Port (AGP) slot.)

I might go with a whole new computer but I'm still thinking about.

[LIST]
My Options
[LIST]
[*]New Computer with PCI slots
[LIST]
[*]New Graphics Card
[/LIST]
[/LIST]
or
[LIST]
New Graphics Card for an AGP slot
[/LIST]
[/LIST]
Thank you again for all your help.
Sincerely,
--Ugeen

However, I continue to get requests to improve my Frames Per Second (FPS) by using an alternative method:  another process, system (i.e. X-Server), setting, etc.

I'm trying to exhaust all avenues before looking into another graphics card and\or computer.  Plus, there's money involved, the lack of money, which allows me plenty of time to modify this system (i.e. crash it).

Would you like something tested to see how it has an affect on my system?  If so, let me know. :)

Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Ugeen on 2008-10-22
> **UltimaDude said:**
> 
What's your performance on XP? I know my old 6200 TurboCache ran WoW really badly, and I'm now on my 9600GT(check specs) it runs worse than Windows but I can get a steady FPS around 60 on high settings.

Hello UltimaDude,

My perforance on Linux \ Wine \ Windows Version: Windows XP, World of Warcraft is playable but the Frames Per Second (FPS) is currently between 5.0 FPS and 10.0 FPS.

My perforance on Microsoft Windows XP, World of Warcraft was playable and even though it was slow, it was faster than it is currently on Linux.  FYI:  I didn't look at the WOW's FPS before installing Linux.

History
I went from Microsoft Windows XP to Linux because I thought that the speed issue that I was noticing was due to Microsoft Windows XP eating up all of my resouces (i.e. memory, hard drive, etc.).  The speed issue was also noticable in other Microsoft Windows XP applications.

I would reinstall Microsoft Windows XP but I had a hard time getting it to use my nVidia GeForce FX 5200 PCI graphics card.  However, I could probably get it to work a lot easier the next time around because I know how to install it now.

...I would like to stay with Linux, if possible.
(FYI:  Installing an operating system (OS) and World of Warcraft (WOW) takes me over 6 hours mostly because of the WOW patches.)

Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by wownerd87 on 2008-10-22
Well if you really dont want to get a new card, in the game go to the effects section and put the settings on low, that should increase it to at least 18-24.

---

### Post by Ugeen on 2008-10-22
> **wownerd87 said:**
> 
Well if you really dont want to get a new card, in the game go to the effects section and put the settings on low, that should increase it to at least 18-24.

Hello wownerd87,

In WOW, my effects are set to low.

Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by wownerd87 on 2008-10-22
> **Ugeen said:**
> Hello wownerd87,

In WOW, my effects are set to low.

Thank you again for all of your help.
Sincerely,
--Ugeen

Sure! No problem. All I do is ask questions on here. I'm glad I can finally give back :D

---

### Post by Eviljim on 2008-10-24
Sorry but I think this isnt going to help

**WARNING: The NVIDIA GeForce FX 5200 GPU installed in this system is supported through the NVIDIA 173.14.xx legacy Linux graphics drivers.** Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more information. **The 177.80 NVIDIA Linux graphics driver will ignore this GPU.** WARNING: You do not appear to have an NVIDIA GPU supported by the 177.80 NVIDIA
Linux graphics driver installed in this system. For further details,please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

And you apparently have all the WoW settings turned down low.

---

### Post by Hire on 2008-10-24
Ugeen your Graphics Card is very very old :(
Stupid questione: do you have disabled compiz before play wow?

---

### Post by Ugeen on 2008-10-25
> **Hire said:**
> 
Ugeen your Graphics Card is very very old :(
Stupid questione: do you have disabled compiz before play wow?

Hello Hire,

To disable Compiz Fusion, I did the following and my Frames Per Second (FPS) went to:  6.4 FPS.  So, I turned it back on.

[LIST=1]
[*]Click on Applications
[*]Click on Settings
[*]Click on Settings Manager
[*]A window appeared with a title of:  Xfce Settings Manager
[*]Click on Desktop
[*]A window appeared with a title of:  Desktop Preferences
[*]Untick Allow Xfce to manage the desktop
[*]Reboot
[/LIST]
Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by Zularan on 2008-10-26
Did you add
```
SET gxApi "OpenGL"
```
to your config.wtf to run under wine in opengl ? 

As well as this regedit addition in the [Howto]("http://ubuntuforums.org/showthread.php?t=579378") ?
> This is a simple registry edit for Wine that will dramatically increase the framerate in game for both ATi and nVidia users.

Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

Notice: the guide below is case sensitive!

1. Find this key HKEY_CURRENT_USER\Software\Wine\
2. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
3. Right-click on the wine folder and select [NEW][KEY]
4. Replace the text New Key #1 with OpenGL
5. Right-click in the right hand pane and select [NEW] then [String Value]
6. Replace New Value #1 with DisabledExtensions
7. Then double click anywhere on the line, a dialog box will open.
8. In the value field type GL_ARB_vertex_buffer_object

---

### Post by Ugeen on 2008-10-27
> **Zularan said:**
> 
Did you add
```
SET gxApi "OpenGL"
```
to your config.wtf to run under wine in opengl ? 

As well as this regedit addition in the [Howto]("http://ubuntuforums.org/showthread.php?t=579378") ?

Hello Zularan,

Yes.

Regarding the code:  SET gxApi "OpenGL" within the Config.wtf file, I've made two shortcuts for testing purposes.
[LIST=1]
[*]OpenGL


[*]d3d
[/LIST]
Plus, I have the following lines of code within the Config.wtf file.

> **Ugeen said:**
> 

.wine \ drive_c \ Program Files \ World of Warcraft \ WTF \ Config.wtf
[LIST]
[*]SET ffxDeath "0"
[*]SET ffxGlow "0"
[*]SET SoundOutputSystem "1"
[*]SET SoundBufferSize "150"
[/LIST]

Regarding RegEdit, it includes the following Strings.

> **Ugeen said:**
> 

Wine
[LIST]
[*]RegEdit
[LIST]
[*]HKEY_CURRENT_USER \ Software \ Wine \
[LIST]
[*]Key:  Direct3D
[LIST]
[*]String:  DirectDrawRenderer
[LIST]
[*]Value Data:  opengl
[/LIST]
[/LIST]
[/LIST]
[LIST]
[*]Key:  OpenGL
[LIST]
[*]String:  DisabledExtensions
[LIST]
[*]Value Data:  GL_ARB_vertex_buffer_object
[/LIST]
[/LIST]
[/LIST]
[/LIST]
[/LIST]

Thank you again for all of your help.
Sincerely,
--Ugeen

---

### Post by glasswalkerny on 2008-10-27
Ugeen,

   Even when that video card was new it was widely accepted that the GeForce 5xxx series cards were the worst thing NVIDIA ever put out.. all of them under performed compared to the 4xxx series cards.. as some people recommended i would upgrade to at least a 6xxx series card or better.. I'm running a 9800gtx card and i still get only about 20fps in Stormwind

---

