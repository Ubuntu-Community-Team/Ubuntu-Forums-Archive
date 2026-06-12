---
title: "nVidia - Graphics card not getting recognised by the kernel"
date: 2007-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by colindfh on 2007-09-11
Hello,

I've just got a new computer and have started running Ubuntu Feisty 7.04 (2.6.20-16-generic ).

Unfortunately I've not had any luck getting the graphics card to work.

# lspci | grep -i nvidia
04:00.0 VGA compatible controller: nVidia Corporation Unknown device 0422 (rev a1)

This is an overview of the hardware I'm using: 

Graphics card: PCI-E nVidia GeForce 8400GS (Point of View).
Motherboard:  ASUS P5LD2-X.
Processor: Intel Core2 Duo E4300 @ 1.8Ghz, 800Mhz FSB
BIOS revision: 0105

I've tried booting from several different Linux distributions and they all have the same problem.

# grep -i nvidia /var/log/Xorg.0.log
(--) PCI:*(4:0:0) nVidia Corporation unknown chipset (0x0422) rev 161, Mem @ 0xdf000000/24, 0xe0000000/28, 0xdc000000/25, I/O @ 0xe800/7, BIOS @ 0xdefe0000/17
(II) Module glx: vendor="NVIDIA Corporation"
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
(--) Chipset Unknown NVIDIA chip found
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Any ideas?

Many thanks!

---

### Post by Cappy on 2007-09-12
Here is the home page so you can read it first : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

```

sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo apt-get install build-essential xserver-xorg-dev
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
sudo dpkg -i envy*.deb
sudo envy -t
```

---

### Post by lsweet on 2007-09-12
I secretly believe Cappy has that macro'd ;)

---

### Post by tza on 2007-09-12
> **Cappy said:**
> Here is the home page so you can read it first : [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

```

sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo apt-get install build-essential xserver-xorg-dev
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb
sudo dpkg -i envy*.deb
sudo envy -t
```

Intel x64, Intel946GZ board, same card, similar problem - 

I have used Envy to install the nvidia driver.  Selecting 2.6.20-16-generic kernel at the grub menu results in no signal at the monitor while loading.

I tried installing the latest kernel this afternoon 2.6.22.6 and reinstalled, thru Envy, the nvidia driver; although I did not purge any previous driver installation - and still the black screen.

Choosing the .20-15 kernel yields no problems (umm, seemingly), although I do see a memory allocation error that flashes so quickly that I can't read it (after grub, before splash).  So my question would be, I suppose, is there a conflict on between dirvers on newer kernels - such as with the default nv driver?

---

### Post by colindfh on 2007-09-13
Sorry for the late reply. Just to say thanks to Cappy - I followed your instructions and it works perfectly.

Thanks!

---

### Post by tza on 2007-09-13
running the same commands as colindfh yields these results:


tza@tza-x64D:~$ lspci | grep -i NVIDIA
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0422 (rev a1)

tza@tza-x64D:~$ grep -i nvidia /var/log/Xorg.0.log
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0422) rev 161, Mem @ 0x52000000/24, 0x40000000/28, 0x50000000/25, I/O @ 0x2000/7, BIOS @ 0xfffe0000/0
(II) Module glx: vendor="NVIDIA Corporation"
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 17:16:40 PDT 2007
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 16:35:28 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(--) Chipset NVIDIA GPU found
(II) Module wfb: vendor="NVIDIA Corporation"
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G86) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.4a.00.05
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic VX1935wm (DFP-0)
(--) NVIDIA(0): ViewSonic VX1935wm (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): ViewSonic VX1935wm (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) NVIDIA(0): Setting mode "1440x900"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) NVIDIA(0): Setting mode "1440x900_60"
(--) NVIDIA(0): No video decoder detected



A) I have no idea what that means -
B) Having said that, it seems the driver is appropriate and recognizes the hardware (for the most part).
C) I ran Cappy's commands, line-at-a-time;  there was no other driver to remove and nothing new to install <<-- this makes sense to me as Envy was my initial attempt at a driver solution.

Ultimately, this isn't critical, simply annoying.  The 2.6.20-15-generic kernel boots with no problems , it is only the newer kernels that have issues.  At heart, I'm really just hoping to understand why it's happening - it would also be nice to optimize for desktop use and take advantage of some of this shiny new hardware!

Any ideas?

---

### Post by dabl on 2007-09-13
> **tza said:**
> 


I tried installing the latest kernel this afternoon 2.6.22.6 and reinstalled, thru Envy, the nvidia driver; although I did not purge any previous driver installation - and still the black screen.



Not quite sure what you're doing -- are you installing Envy and then running it with ```
sudo envy -t
``` all from the console?  Although the new version of Envy is pretty self-sufficient, you might want to install the packages linux-headers-'uname -r' and build-essential for your new kernel, just to be sure they are there.  And you might want to have Envy first "uninstall the Nvidia driver" just in case there are some residuals from prior attempts that are in the way.

:)

---

### Post by tza on 2007-09-13
I was attempting to illustrate that any kernel newer than 2.6.20-15 would not boot properly, and that I didn't seem to have other residual driver junk on the system with my statement.

I've run Envy from Applications > System Tools > Envy as well as text mode.
I've uninstalled the NVIDIA driver.
I've cleaned the system of all nvidia drivers (option 6-ish?).

I still have no signal at the monitor after the grub selection screen when choosing newer kernels.  Bummer.

I do notice my xorg.conf has a 'generic' monitor and 'generic' video card after running Envy (and selecting 'Y' to auto-update the xorg.conf).  The nvidia-settings app, however, has accurate and precise info agout my hardware and monitor. I'm baffled.  Maybe hand configure the xorg.conf?

Thanks for helping

---

### Post by dabl on 2007-09-13
> **tza said:**
> 

  Maybe hand configure the xorg.conf?



Before you do that, in the console give it ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
``` 

This will write over your xorg.conf with settings that the nvidia driver can detect on your system, plus set it up for glx and compositing, in case you want to try compiz.

:)

---

### Post by tza on 2007-09-13
[SOLVED]

I may be an idiot.  

While un- and re-installing the nvidia driver, I spotted in the (raipidly) scrolling text that the driver module was being built in a kernel-specifc manner.  I anticipated that the driver modules would be generally universal and load into whatever kernel happened to ask.  Seems not.

So - while in X, dpkg-reconfigure for xserver, choose the vesa driver
reboot into newer kernel - get a hacked up desktop, but a desktop nonetheless.
run Envy (thank god for this tool!) - reboot
dpkg-reconfigure again (gotta pick the proper resolution mode).
reboot.
Hey, it works!

All of you out there with a clue are now wondering exactly how I got into this mess in the first place.  So am I.  
Intel board - built in GMA w/analog input.  No DVI.  
geforce 8400 -no analog input.  DVI.

Somewhere in finding the original desktop after installing from live cd caused this problem.

For anyone else just installing and using current nvidia cards, I say - don't try so hard to break stuff that doesn't need to be broken.  And use Envy.

*off to donate to Envy project*

Thanks everyone for helping out and posting output and commands - seeing it all helped me solve this difficulty - PBKAC.

---

### Post by jeepescu on 2007-09-19
Thanks cappy.
The procedure worked fine for me too.

---

