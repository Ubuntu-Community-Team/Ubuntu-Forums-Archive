---
title: "Can't get wifi to work on new toshiba laptop"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by AlanGard on 2008-07-21
Hi, I'm trying to use wifi on my new Toshiba Satellite A305D laptop. In the hardware drivers tool it says That support for Atheros 802.11b wireless lan card is enabled and in use but it does not seem to be working. Can anyone help me?

I'm using 8.04.

---

### Post by Tlingit on 2008-07-21
Hello I will help you. do you still need assistance?


and a, 

lsusb

lsmod

---

### Post by stchman on 2008-07-21
> **AlanGard said:**
> Hi, I'm trying to use wifi on my new Toshiba Satellite A305D laptop. In the hardware drivers tool it says That support for Atheros 802.11b wireless lan card is enabled and in use but it does not seem to be working. Can anyone help me?

I'm using 8.04.
Give us an lspci output here in this thread.

---

### Post by Meltedfusion on 2008-08-04
Hello Everyone,

I am having the same issue as well. I have a Toshiba Satellite laptop A215 running I believe its Hardy 8.04
I cant my wifi to work either.
I read the previous post and here is my lspci info: 

em@em-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
em@em-laptop:~$ 

Any help will greatly be appreciated.
I look forward to your response.

---

### Post by pgte3 on 2008-08-04
I am currently running 32 bit Ubuntu 8.04, but this link I posted awhile ago may be helpful:

[http://ubuntuforums.org/showthread.php?t=861683](http://ubuntuforums.org/showthread.php?t=861683)

I have not started to play with 64 bit yet, let me know how if this works.

---

