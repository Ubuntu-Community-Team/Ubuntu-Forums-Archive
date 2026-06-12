---
title: "8800 GT - driver loaded, no devices found"
date: 2008-06-25
forum: x86 64-bit Users
---

### Post by man_bash on 2008-06-25
Hello everybody

I have an EVGA Nvidia GeForce 8800 GT (G92), with Hardy 64-bit, Gnome.
I have a persisting problem with installing a driver for the video card. So far I have tried all drivers from nvidia from 169.12 to 177.13, as well as envyng with 169.12 and 173.14, as well as enabling the restricted driver from Administration panel. Every time I load any driver the screen turns off at the point of loading X. The loading line completes and screen turns off, unresponsive to keyboard, and must be hard-rebooted. 
/var/log/dmesg.0 has this in it

[   38.414788] nvidia: module license 'NVIDIA' taints kernel.
[   38.694018] ieee80211_crypt: registered algorithm 'NULL'
[   38.712442] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   38.712445] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   38.870964] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[   39.004087] zd1211rw 1-4:1.0: eth0
[   39.004102] usbcore: registered new interface driver zd1211rw
[   39.025599] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   39.025609] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   39.025616] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   39.025755] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.05  Mon May 19 00:03:22 PDT 2008
[   40.094821] lp: driver loaded but no devices found


Any ideas?

Thank you

---

### Post by stchman on 2008-06-25
> **man_bash said:**
> Hello everybody

I have an EVGA Nvidia GeForce 8800 GT (G92), with Hardy 64-bit, Gnome.
I have a persisting problem with installing a driver for the video card. So far I have tried all drivers from nvidia from 169.12 to 177.13, as well as envyng with 169.12 and 173.14, as well as enabling the restricted driver from Administration panel. Every time I load any driver the screen turns off at the point of loading X. The loading line completes and screen turns off, unresponsive to keyboard, and must be hard-rebooted. 
/var/log/dmesg.0 has this in it

[   38.414788] nvidia: module license 'NVIDIA' taints kernel.
[   38.694018] ieee80211_crypt: registered algorithm 'NULL'
[   38.712442] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   38.712445] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   38.870964] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[   39.004087] zd1211rw 1-4:1.0: eth0
[   39.004102] usbcore: registered new interface driver zd1211rw
[   39.025599] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   39.025609] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   39.025616] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   39.025755] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.05  Mon May 19 00:03:22 PDT 2008
[   40.094821] lp: driver loaded but no devices found


Any ideas?

Thank you

Did you try enabling the restricted driver?  Also you could install the following package:

```
sudo apt-get install nvidia-glx-new
```

For hardy the nvidia-glx-new is the 169.12 driver.

I have an 8800GT and it works perfectly with Hardy.

---

### Post by jocko on 2008-06-25
> **man_bash said:**
> [   38.414788]nvidia: module license 'NVIDIA' taints kernel.
...
[   39.025755] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.05  Mon May 19 00:03:22 PDT 2008
[   40.094821] lp: driver loaded but no devices found

There are no errors there, just friendly messages. The lp module has nothing to do with nvidia (I'm not sure what it is, but as it depends on the module parport, I guess it have something to do with printers or other devices that you connect to parallell ports).

To find errors in xorg, you need to check /var/log/Xorg.0.log.
List errors:
```
cat /var/log/Xorg.0.log | grep EE
```List warnings:
```
cat /var/log/Xorg.0.log | grep WW
```When the screen goes black, is the display put to sleep mode?
In that case perhaps xorg is trying to use a resolution or sync / refresh rate that your display can't handle.

Try to find your monitors specifications (especially the horizontal sync and vertical refresh rate ranges it supports).
Then boot to recovery mode and try this:
```
nano /etc/X11/xorg.conf
```
Find the monitor section and add your correct sync/refresh rates as below (red text):
```
Section "Monitor"
[COLOR=Gray]        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Q910"
        Option      "DPMS" "true"[/COLOR]
[COLOR=Red]        HorizSync    30-110
        VertRefresh  50-150[/COLOR]
EndSection
```

---

### Post by man_bash on 2008-06-26
@ jocko

OK, I tried all as suggested. Still doesn't work.
errors of Xorg.0.log

```

(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

warnings
```

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) ****INVALID MEM ALLOCATION**** b: 0xce000000 e: 0xce000000 correcting
(WW) Configured Mouse: No Device specified, looking for one...

```

Also, I did have to manually edit the xorg.conf file to the monitor's specs

```

        [color=red]HorizSync    30-110
        VertRefresh  50-150 [/color]
to 
        [color=#00ff00]HorizSync    30-96
        VertRefresh  50-160[/color]


```

I know that the monitor will do at most
2048x1536 @ 60 Hz
1600x1200 @ 75 Hz
1280x1024 @ 85 Hz
1024x768 @ 100 Hz
Should I put them in the xorg.conf too?

xorg.conf (generated by 177.13 driver), with edit
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Tue Jun 10 17:10:22 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
When the screen goes black I cannot determine if the monitor is in a sleep mode or the regular off state, but the screen itself is off. What worries me most is that the computer completely stops responding, even "Caps Lock" light will not light on.

Anything else I should try?

---

### Post by jocko on 2008-06-27
Try changing your screen section to:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        [COLOR=Red]Modes       "1280x1024" "1024x768"[/COLOR]
    EndSubSection
EndSection
```Put your preferred resolution first in that line, followed by any other resolutions you want to be able to set.
The error regarding the glx module may be a problem. I have no idea what could cause that.
To fix the warning about the mouse, try changing from:```
"Device"  "/dev/psaux"
```to:```
"Device"  "/dev/input/mice"
```The fact that not even the caps lock indicator works may indicate a serious problem somewhere else, such as a kernel freeze or a hardware malfunction.
Can you force a safe reboot by pressing Alt+SysRq+R, Alt+SysRq+S, Alt+SysRq+E, Alt+SysRq+I, Alt+SysRq+U, Alt+SysRq+B (press one key combination, wait a few seconds and then press the next one)?
When you press Alt+SysRq+B your computer should reboot unless you have a complete kernel or hardware lockup.

---

### Post by man_bash on 2008-06-30
OK
Mouse is not really an issue, but thank you for the fix anyway :D

lp message - I had to disable Parallel Port in BIOS because the motherboard decided to share the IRQ between the LP and the Video Card. I do not use it anyway, but I like to have a dedicated IRQ for the video card, and some suggested that sharing IRQ between video card and other device might have posed a problem. I have also disabled Serial port and onboard LAN (As neither is used) to free up IRQs.

Now back to the video card

I added the "Modes" line 
```

Modes    "1600x1200" "1280x1024" "1024x768"
``` (I use 1600x1200 all the time)

The screen still turned off when I booted. ](*,)

Alt+SysRq+R, Alt+SysRq+S, Alt+SysRq+E, Alt+SysRq+I, Alt+SysRq+U were all tried, in 10 second intervals, and brought no result whatsoever

Now, on the lighter side, Alt+SysRq+B DID reboot the computer. 

I also forgot to mention that when I tried starting X from manually navigating to /etc/X11, it gave me an error "Driver loaded but no compatible Nvidia hardware found" (or something very much to that effect). 

Here are the detailed system specs if needed

Mobo: DFI Infinity NF4X
CPU:  AMD Turion ML-30 (OC to 2.5 GHz)
Ram:  1024 Kingston Value RAM + 1024 Buffalo Value Select RAM, both DDR400 (At approx. 209 MHz, 1T timings, 3-3-3-8, Asynch/scew at 10/7), rock stable in Memtest86+
HDD:  320 GB WD SATA (primary) + 250 GB Maxtor PATA (Win2K dinosaur with data)
PSU:  I got 2 hooked up, 500W for the main system, 350W for the PATA HDD and the DVD burner (thought that 25 amps on 12V rail might have been a little too few, but that is not the case, just too lazy to remove the 350W PSU given all the work I had to do to put it in)

I have removed the overclocks for the testing of the driver, same result.](*,)

---

### Post by jocko on 2008-06-30
> **man_bash said:**
> Alt+SysRq+R, Alt+SysRq+S, Alt+SysRq+E, Alt+SysRq+I, Alt+SysRq+U were all tried, in 10 second intervals, and brought no result whatsoever

Now, on the lighter side, Alt+SysRq+B DID reboot the computer.
That's exactly what's supposed to happen:
R gives the keyboard acces to the kernel (you'll probably not notice any effect)
S syncs all mounted filesystems so they can be safely unmounted (you may notice that the harddrive starts working)
E Kills all running processes except init (you'll probably not notice any effect)
I kills init (you'll probably not notice any effect)
U remounts all filesystem in read-only mode (you'll probably not notice any effect)
B reboots the computer
(if you don't run the other combinations before alt+sysrq+b, there's a risc of file system corruption or loss of data in open files).
This is a safe way of rebooting instead of using the power or reset buttons, but it works only if the kernel is still working.

So if your computer did reboot, that means it was not frozen.
The only thing I know which causes this is if your graphics card tries to use a resolution/refresh rate combination that your monitor can't handle.
Some monitors will display a message "out of sync" or something similar, while others (like mine) will just go into standby mode.

If you have tried both of my previous advice, I have no clue what's causing it, but my guess would be that if you google for this error you may find a fix:
```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

---

### Post by man_bash on 2008-07-02
OK, found this in nvidia-installer.log
```

 No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-19-generic/build'
-> Kernel output path: '/lib/modules/2.6.24-19-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-19-gener
   ic/build SYSOUT=/lib/modules/2.6.24-19-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-19-generic/build SUBDIRS
   =/tmp/selfgz9305/NVIDIA-Linux-x86_64-177.13-pkg2/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)

```

Would this mean that the kernel interface doesn't even compile eproperly?

---

### Post by PmDematagoda on 2008-07-02
Did you install the necessary packages for the Nvidia installer with:-
```
sudo apt-get install build-essential
```
?

---

### Post by jocko on 2008-07-02
> **man_bash said:**
> ```
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)

```Would this mean that the kernel interface doesn't even compile eproperly?

That looks perfectly fine to me...
What you see here is just a script that is run during the install process, designed to check that you have the file autoconf.h or auto.conf in your kernel source, and if it would be missing it would stop the installer at this point and show you this message:
```

  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


```What you see are the actual commands (the lines starting with "echo") which would show that message, not the actual message.

---

### Post by man_bash on 2008-12-30
Ok, my friend has a XFX nVidia 8600 GTS which I was able to borrow from him temporarily. I gave him my 8800GT in the meanwhile. Again, tried installing the driver with envy. Again, the same problem . I think that the problem here is with the motherboard (although I do not know why, even the chipset is nVidia nForce 4...). It is either with the chipset driver, or alternatively something is not clicking right when trying to connect a PCIe 2.0 board with my PCIe 1.0 slot. Both video cards work fine(ish) in windows 2000 (both seem to overheat enough for a shutdown after 3-5 hours of Oblivion, never mind my 6 case fans). I will try another motherboard I have kicking around, MSI K8N Neo3, although it also has the nForce 4 chipset.

---

### Post by soxs on 2009-01-01
```
lp: no devices found

``` _**IS NOT RELATED TO ANY NVIDIA BINARY DRIVER!**_ It's for parallel or printer port or something like that, my machines with intel and amd gpus report the same message.

---

### Post by man_bash on 2009-06-01
Ok, the problem has been solved by upgrading to Ubuntu 9.04. I even played Counter-Strike through Wine yesterday. Yay!

---

