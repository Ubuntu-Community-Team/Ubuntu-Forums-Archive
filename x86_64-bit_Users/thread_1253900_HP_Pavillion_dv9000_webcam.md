---
title: "HP Pavillion dv9000 webcam"
date: 2009-08-30
forum: x86 64-bit Users
---

### Post by dan724 on 2009-08-30
Hello all, I recently installed ubuntu 9.04 on my HP Pavillion dv9000. This laptop uses an amd64 processor. This laptop comes with a built in webcam above the screen. I have not been able to get this webcam to work. I believe I am missing kernel drivers for it (correct me if I'm wrong). The file "/dev/video0" does not exist. I have loaded the kernel modules v4l2_int_device, v4l2_common, v4l1_compat, uvcvideo, and videodev. I have tried using aMSN, Ekiga, Camorama and Cheese to access the webcam. None of them see the webcam. I have found the following drivers: [http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/) however those are for an old kernel and I would really prefer not to downgrade my kernel just to get my webcam working. I'm also not even sure the deb packages there would work as they are for an i386 and this laptop is an amd64. Can anyone get my webcam working?

The following is the output of lsusb:
```
joel@joel-laptop:~$ lsusb
Bus 002 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd 
joel@joel-laptop:~$
```and this is the output of lspci:
```
joel@joel-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
joel@joel-laptop:~$ 

```

---

### Post by tgeer43 on 2009-08-30
This won't actually solve your problem but it's something that you should know anyway.

I have an HP DV9500T and have fresh installed 9.04 64-Bit twice and both times the webcam worked right out of the box so you shouldn't be missing any packages, kernel modules, etc. It's more likely to be a configuration error.

I'll be thinking on this but in the meantime if you want to compare anything between our two machines, just let me know.

tgeer

p.s. I do have a 'video0' file in /dev.

---

### Post by dan724 on 2009-08-31
what webcam does that laptop have? is it the 05ca:1810 Ricoh that shows up in my lsusb?

---

### Post by tgeer43 on 2009-08-31
Good question. Oddly enough it does not show up at all in 'lsusb'. I then ran 'hardinfo' and it doesn't show up under USB devices. It does show up under Input Devices but only in the most generic terms.

After doing some reading I discovered that the DV9500T actually has a *downgraded* webcam compared to the DV9000. It seems that HP was having framerate issues with the 1.3 Megapixel webcam in the DV9000 and opted for a VGA resolution (640x480) one for the DV9500T.

That's what I get for assuming again. :wink:

Don't laugh but I bought this DV9500T as soon as it was released. I ordered it special with every single component upgraded to the max and paid over $3000. And for that I get a *downgraded* webcam.

But hey, at least it works!

tgeer

---

