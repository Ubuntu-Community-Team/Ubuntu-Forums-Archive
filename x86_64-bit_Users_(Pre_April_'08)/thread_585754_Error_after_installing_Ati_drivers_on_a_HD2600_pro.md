---
title: "Error after installing Ati drivers on a HD2600 pro video card on Gutsy 64"
date: 2007-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by lekazo on 2007-10-21
Hi everyone

I´m having problems installing my Ati/AMD HD 2600 Pro video card with Gutsy_64. I tried using the Restricted Drivers tool and downloading and installing the driver from the AMD web site, but nothinng works.

The problem is the same in both cases, and hapens when I install the video card drivers. After reboot my PC and when Ubuntu restart, no image apears in the screen. Also the key combinations Ctrl-ALT-Fx or Ctrl-Alt-backspace are useless, so I have to use the reset botom.

My PC configuration is this:

Athlon X2 4000+ Processor
MSI AMG2 Mother Board
1Gb DDR2 - 667 Kingston Memory
Ati/AMD HD 2600 Pro 512 VRAM DDR2  Saphire Video Card
200Gb SATA Maxtor Hard Disk

Thanks for any help

---

### Post by b4d on 2007-10-28
Same thing at my friends laptop, and every cca 15x reboot works ok.

---

### Post by b4d on 2007-10-29
The older drivers prom ati solved the issue.

---

### Post by lekazo on 2007-10-29
Well, I proved the last version, 8.42.3-x86.x86_64, and the previous one, but the problem is the same one in both cases. Gnome only works when I use Mesa. Is something strange because with Festy everything worked well. Any idea?

Also I tried this howto, but was useless 

[http://ubuntuforums.org/showthread.php?t=575843&highlight=hd+2600+pro](http://ubuntuforums.org/showthread.php?t=575843&highlight=hd+2600+pro)

---

### Post by Krommbuntu on 2008-02-03
After a few months of trying off and on to get this working myself I have been unsuccessful.  I originally had feisty installed and never bothered with getting ati drivers working so I don't know if it worked there but I have since upgraded to gutsy.  I have followed every possible guide I have found in an attempt to get it working.  I have tried using envy and always results in the same thing.  It all appears to install fine and then when I reboot after the initial ubuntu splash/loading screen I get a black screen with the round loading image in the center of the screen that is frozen.  For reference I am using an HD2600XT video card from sapphire and an ASUS P5K motherboard with a c2d 2160 cpu.  

Is there perhaps a chance that there are some settings in the motherboard I should set that I'm not seeing?  Or am I out of luck at this point?

---

### Post by GiTMaN on 2008-02-08
I found the best way to install this grafix driver with Ubuntu 7.10 is to do the following...

AFTER A FRESH NEW INSTALL DO THE FOLLOWING....

First update your system.. dont install or make any grafix drivers work at this stage.
Once you rebooted download Envy [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I downloaded the .run file and converted to a .deb using alien package.In the Terminal the command is: 
sudo alien -k <file name>   
(Terminal is in Tab-- Applications/accessories)

this should convert it to a .deb file which you can open with the built in archive manager.
Don't open the file just yet!
If you don't have alien download it from the Synaptic Package Manager...
The Synaptic Package Manager is in the Tab--System/administration and you can run a search for "Alien"

First type these commands in the terminal:
sudo apt-get install xorg-driver-fglrx
sudo apt-get install xorg-driver-fglrx-dev

ok now run the envy software and install the program and run the app.
I would go with installing ATI drivers automatically (If you have probs do it manually the 8.01 version worked with me)
Let Envy do its thing and agree to let it download dependencies and setup your xorg.conf

Reboot

Hopefully you should have booted up with better gfx settings....
Now go into Synaptic Package Manager and download the compizconfig-settings-manager
it should already be built in but its not... I don't know why but mine wasn't.

This is the way I got my Ubuntu to work (although I think its not running 100%)
All the effects work, 3D cube etc etc. 

Good Luck

---

### Post by Krommbuntu on 2008-02-09
Gitman could you post your computers specs? I'm curious to see if we can narrow this down to a hardware compatibilty issue between people that have gotten these hd2600 series cards work and those that can't?

---

### Post by kokotero on 2008-02-16
Not working for me either, Proved Ubuntu way/Ati way both on gutsy and Hardy. Have not proved envy.

MY SPECS:

Graphic card:
SAPPHIRE HD 2600 PRO (AGP version)
lspci output: 01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9587

CPU:
Intel(R) Pentium(R) 4 CPU 2.00GHz

Restricted manager doesn't not give option to install any restricted drivers. After putting fglrx driver and rebooting I always get a black screen. Doing alt+f7 shows "fglrx (8.455.2): Already installed on this kernel". Proved with fresh install too.

I'll try with envy following GiTMaN's post.

Grrrr, ATI!!!!!!!!!!!!!!!!!!!!!! (so frustating buying a new card thinking I would able to use and spending hours with no result!!)

I hope this helps, nice job admins&posters

Eneko

---

### Post by kokotero on 2008-02-16
No luck with envy, which I think installs ati-driver-installer-8-01.

I proved too with ati-driver-installer-8-02 and ati-driver-installer-8.42.3. The later gives black screen and blocks the system.

---

### Post by mtxcoll on 2008-06-20
> **kokotero said:**
> No luck with envy, which I think installs ati-driver-installer-8-01.

I proved too with ati-driver-installer-8-02 and ati-driver-installer-8.42.3. The later gives black screen and blocks the system.

Bump... I'm having the exact same problem with a dual-core 64-bit ATI card and ATI HD2600 Pro. I was able to get the fglrx driver working on the first restart but I could only get a blank screen in subsequent sessions. After several reinstalls using envy and the official Ubuntu version I'm totally lost... :(

---

