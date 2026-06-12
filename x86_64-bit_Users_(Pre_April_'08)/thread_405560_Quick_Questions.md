---
title: "Quick Questions"
date: 2007-04-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by rivera151 on 2007-04-09
Hi.  I'm trying out Ubuntu and Linux.  I installed a 32-bit Ubuntu on my HP (x64) laptop.  Everything worked allright; just the usual issues with the Broadcom 4318 (resolved) and with the ATI Radeon 200M XPRESS card (unresolved).  Since it looks like I might be be dealing with the card for a while, and since I'd like to (someday?) a contribute to the Linux community (I can program in C quite well), I decided to go ahead and delve into the x64 distro.

Well, its a bit of a rocky start, but here I am, and I'm not turning back (not after seeing Vista, yikes!).  

My first inquiry is mostly from my lack of knowledge of the kernel-module architecture:
I decided to install the ATI driver but it's not working.  I'm defaulting to my original Mesa driver.  Since I'm not using the driver I would like to uninstall it.  I will write down my procedure and ask, since I am uncertain if this is correct:

- run the command "sh ./ati-driver-installer-8.34.8.run" (ATI site says this file is there, I haven't seen it)
- replace my xorg.conf file with the original (or should I just run "sudo dpkg-reconfigure xserver-xorg"
- reboot

When the ATI installer was compiling the kernel module, it warned about having to recompile the kernel for every upgrade.  Does this mean I also have to revert to the previous kernel also befor rebooting, or am I just way off here?

Thank you for you time.

---

### Post by Lonthong on 2007-04-09
This [wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") guide always works for me. Otherwise, try the [official help guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

After kernel upgrade just boot into the new kernel & recompile the driver as follows:
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx-kernel
sudo module-assistant install fglrx-kernel
sudo depmod -a

---

### Post by totalnub on 2007-04-09
hey, do you happen to have a hp pavillion zv6000 laptop?
if so, i have the perfect guide for you. [http://ubuntuforums.org/showthread.php?t=321766](http://ubuntuforums.org/showthread.php?t=321766)
it works like a charm. gl man.
```
clay@claylap:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6234 (8.32.5)

```

---

### Post by rivera151 on 2007-04-10
You are right on, totalnub ... zv6000 it is.  I followed that post both on 32-bit and 64-bit install but could't get it to work (I had Sideport only, eg. dedicated video ram)  Did you get it to work on a 64-bit install?  Also, did you download the latest ati driver or did you use the link on that post (8.32.5)?

Lonthong: I have also tried the wiki and the official help guide without luck.  However, most guides are not that different from each other.  I guess I am just being unlucky.  Also I don't think you understood my question (maybe I didn't explain correctly).  My concern is not If I should recompile the kernel with the fglrx module; that I've done.  My concern has to do with the fact that IF I uninstall the fglrx kernel module, do I have to revert to the kernel I had before installing fglrx?

---

### Post by ffxr on 2007-04-10
> My concern has to do with the fact that IF I uninstall the fglrx kernel module, do I have to revert to the kernel I had before installing fglrx?


no, the warning you see is just saying that you have to reinstall the flgrxr driver anytime you update your kernel. it doesnt matter if you uninstall it from your kernel.. it wont break anything.. if thats what your worried about..

---

### Post by rivera151 on 2007-04-10
> **ffxr said:**
> no, the warning you see is just saying that you have to reinstall the flgrxr driver anytime you update your kernel. it doesnt matter if you uninstall it from your kernel.. it wont break anything.. if thats what your worried about..

Thanks.  That's exactly what I was worried about regarding the kernel module.  Good to know. :lolflag:

---

### Post by totalnub on 2007-04-10
yea, i am currently running beryl in ubuntu 6.10 64. i used (and am still using) the driver from that howto.
you need to have only sideport....128MB in your bios. other than that, it works.....the new drivers gave me issues when i tried to logout.
let me know what is goin on.....btw what post did you use to get your wireless working?.....also the 6.10 liveCD doesn't work as i'm sure you know.....

---

### Post by totalnub on 2007-04-10
also are you sure that you have a 4318 card? my output of lspci is:
```
clay@claylap:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by rivera151 on 2007-04-11
Yep. It's a zv600. The main players here are the AMD64, the Broadcom 4318, and the ATI Rad 200M (PCI Express version). I see that you have a different wireless in your output; I'm assuming you and I have the same model computer but with different wireless adapters. I'll doublecheck my output and post it once I get home, but I'm 100% positive I have a 4318.
 
And like I said, I got my wireless working on the 32-bit version of Ubuntu; I have not been able to get it to work on my 64-bit install. But I got my wireless working on 32-bit Ubuntu using the following post:
 
Title: **HOWTO: Broadcom 4318 Wireless Cards **
url: **[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)**
 
I'm gonna try using the driver on the post you referred me to and tell you my result.  We should keep in touch also, as things develop, especially with Feisty around the corner.

---

### Post by rivera151 on 2007-04-14
totalnub: I uninstalled the driver and followed your advice, including downloading the driver you suggested.  Works like a charm!  Thanks for the tip.  Now we need to get the wireless working.  I think I read somewhere that ndiswrapper won't work with the current x64 kernel version, and that there are some alternate kernels that we miht need to install.  Have you had any progress getting wireless working?

Oh, by the way, I typed into the console 

```

lspci | grep broadcom

```

and I get the following:
```

03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by totalnub on 2007-04-24
sorry i haven't gotten back with ya sooner. grats on geting the 200m working. :)  I'm not goin fiesty just yet. still the same problems (wireless, 200m), but no solutions as of yet. all of a sudden my wireless stopped working.....arg.....guess i'm gonna have to do that whole deal over again....psh. 

=====edit======
SWEET. WIRELESS!!!!
i don't know if it is the same for you, but if you are running into the problem of not finding any networks, but you have the drivers installed and whatnot. try adding the boot cheatcode "irqpoll" to /boot/grub/menu.lst. works like a charm. i guess that somehow my menu.lst got changed without my knowledge....oh yea, stupid SUM (Start Up Manager)....psh.... anywho, gl man.

---

