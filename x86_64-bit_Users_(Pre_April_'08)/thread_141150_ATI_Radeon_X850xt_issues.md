---
title: "ATI Radeon X850xt issues"
date: 2006-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by mckeja on 2006-03-07
I'm using a Radeon X850xt AGP video card on an ABIT AV8 motherboard.  At first, I followed the steps listed in the first portion of [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI).  This met with no success, so I tried the second portion: Using drivers from ATI.  Again, no success.

Through searching the forums, googling, and various brainwracking, I finally managed to get X to use 'fglrx' device instead of 'ati.' However, neither 'fglrx' nor 'ati' gives me hardware 3d rendering.  

modprobe fglrx returns:
[INDENT]FATAL: Error inserting fglrx (/lib/modules/2.6.12.070306/misc/fglrx.ko): No such device
[/INDENT]

Xorg.0.log output: 
[INDENT]grep '(EE)' < /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) fglrx(0): === [R200DALSetControllerConfigForRemap] === CWDDC ControllerSetConfig failed: 6 - 0
(EE) fglrx(0): === [R200DALSetControllerConfigForRemap] === CWDDC ControllerSetConfig failed: 6 - 0
[/INDENT]

lspci info:
[INDENT]lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4b49
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4b69
[/INDENT]

My current device section (xorg.conf):
[INDENT]Section "Device"

        Identifier  "ATI Radeon X850 XT"
        Driver      "fglrx"
#       ChipID      0x4a50
        ChipID      0x5d52
        Option      "UseFastTLS" "2"
        Option      "BlockSignalsOnLock" "on"
        Option      "UseInternalAGPGART" "no"
        BusID       "PCI:1:0:0"
EndSection
[/INDENT]

Also: 
[INDENT]Section "Module"
        Load  "GLcore"
        Load  "bitmap"
        Load  "ddc"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "type1"
        Load  "vbe"
        #Load   "dri"
EndSection
[/INDENT]

Note that both ChipID 0x4a50 and 0x5d52 will let 2d work. Setting it to what lspci returns, 0x4b49, results in 'Fatal: No devices found.'  0x5d52 is the chip listed for the X850xt in ATI's supported list, and 0x4a50 is the ChipID for the X800. Also, I have tried "UseInternalAGPGART" "yes" with no different results.  I've tried custom compiling a kernel with framebuffer items completly disabled (as someone somewhere said it could interfere with ATI's driver, and that did not help any either.

From what I can determine, it appears that the X850xt AGP uses a different chipset ID than the PCIE, but ATI's linux drivers only match the PCIE chip ID's to the X850xt.  Is there some workaround that I can do to get hardware 3d rendering to work?  FWIW, I have also tried installing 32-bit linux instead of 64-bit, and had the same results.

---

### Post by Zeroedout on 2006-03-08
well, since those methods of installing ati's drivers did not work, I can explain my own method to you. Mind you, it is a very strange method that very few people choose to use, but perhaps it willl work for you. I install the ati drivers with a normal install, all default options. It compiles and copies fglrx.ko to /lib/modules/<kernel>/kernel/drivers/char/drm/fglrx.ko so i copy this over to /lib/modules/<kernel>/kernel/drivers/video/  and it when i restart X, it works. strange thing is, with 8.22.5, if i rename fglrx.ko in ...../char/drm it won't work, and if it is not present in .../video it doesn't work either. I'm sure there's a rational explaination, but still, strange eh?

---

### Post by Zeroedout on 2006-03-10
haha, i just realized why you couldn't get it working, it was not supported in 8.22.5! But, you are in luck, 8.23.7 was JUST released, and it supports the x800/x850. Try installing 8.23.7 and it should work

---

### Post by mckeja on 2006-03-11
Thanks for the heads-up. I'll try it first thing in the morning and let you know the results.


Edit:

Yep, the 8.23.7 worked just fine. More or less. Still got some wierd issues, but they may be related to stuff I was trying to get it working earlier.

---

