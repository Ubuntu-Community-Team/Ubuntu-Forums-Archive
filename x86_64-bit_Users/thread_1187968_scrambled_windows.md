---
title: "scrambled windows"
date: 2009-06-15
forum: x86 64-bit Users
---

### Post by jayanramesh on 2009-06-15
Dear pals
My windows frequently freezes and it gives the look as if it was scrambled.Could anybody help me to get rid of this prob..I have attached the screen shot of window how it looks like.

---

### Post by markharding557 on 2009-06-17
looks like a video driver problem.
what driver are you using on what hardware?

---

### Post by jayanramesh on 2009-07-22
Dear markharding557,
My comp. conf. is intel core 2 quad - Q9400 and the main board is intel DG 43NB with 4GB DDR2 800mhz RAM.
Thank you.

---

### Post by brianfactors on 2009-07-23
That didn't tell us much about your vid card. Could you please run:
```
lspci
```

And post the output?

---

### Post by djchandler on 2009-07-23
I had a similar problem using the fglrx driver with the ATI Radeon HD 3200 GPU. I gave up on the repositories getting this fixed and used ATI's installer. I think there's a problem in Jockey, but that's just a guess. Using the ATI installer (not synaptic or apt-get) overrides the available video modes for your monitor being reported by Jockey (I think).
 
Here's my current xorg.conf after using ATI's installer:
 
> Section &quot;ServerLayout&quot;
    Identifier     &quot;aticonfig Layout&quot;
    Screen      0  &quot;aticonfig-Screen[0]-0&quot; 0 0
EndSection
 
Section &quot;Files&quot;
EndSection
 
Section &quot;Module&quot;
EndSection
 
Section &quot;Monitor&quot;
    Identifier   &quot;Configured Monitor&quot;
EndSection
 
Section &quot;Monitor&quot;
    Identifier   &quot;aticonfig-Monitor[0]-0&quot;
    Option        &quot;VendorName&quot; &quot;ATI Proprietary Driver&quot;
    Option        &quot;ModelName&quot; &quot;Generic Autodetecting Monitor&quot;
    Option        &quot;DPMS&quot; &quot;true&quot;
EndSection
 
Section &quot;Device&quot;
    Identifier  &quot;Configured Video Device&quot;
EndSection
 
Section &quot;Device&quot;
    Identifier  &quot;aticonfig-Device[0]-0&quot;
    Driver      &quot;fglrx&quot;
    BusID       &quot;PCI:1:5:0&quot;
EndSection
 
Section &quot;Screen&quot;
    Identifier &quot;Default Screen&quot;
    Device     &quot;Configured Video Device&quot;
    Monitor    &quot;Configured Monitor&quot;
EndSection
 
Section &quot;Screen&quot;
    Identifier &quot;aticonfig-Screen[0]-0&quot;
    Device     &quot;aticonfig-Device[0]-0&quot;
    Monitor    &quot;aticonfig-Monitor[0]-0&quot;
    DefaultDepth     24
    SubSection &quot;Display&quot;
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
 
Here's the entirety of xorg.conf when it scrambles the screen:
 
> Section &quot;Device&quot;
    Identifier    &quot;Configured Video Device&quot;
EndSection
 
Section &quot;Monitor&quot;
    Identifier    &quot;Configured Monitor&quot;
EndSection
 
Section &quot;Screen&quot;
    Identifier    &quot;Default Screen&quot;
    Monitor        &quot;Configured Monitor&quot;
    Device        &quot;Configured Video Device&quot;
EndSection
 
Word of caution: don't use the ATI installer unless you are comfortable running commands from the terminal. 
 
The ATI Installer is available at:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
 
Also see the Ubuntu Forums thread at:
[http://ubuntuforums.org/showthread.php?t=1133950](http://ubuntuforums.org/showthread.php?t=1133950)
 
I'm now using the 64-bit version of ATI installer 9.06
 
Best of luck!

---

### Post by jayanramesh on 2009-07-24
Dear brianfactors,

> Here is the output"[QUOTE]jayanr@jayanr-me:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
04:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
jayanr@jayanr-me:~$[QUOTE][QUOTE][/QUOTE][/QUOTE][/QUOTE]

---

