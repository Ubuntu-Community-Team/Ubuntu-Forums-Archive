---
title: "redetect hardware after mainboard switch?"
date: 2007-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by nutz on 2007-12-29
I swapped out my mainboard today and I think I need to re-detect some hardware because when I open up the hardware information panel now it shows a ton of unknown hardware. The PC runs just fine since both the old mainboard and the new one have Nvidia based chipsets all I had to do was re-enable the restricted driver. But what about all this other stuff in there that comes up as unknown? There was no unknown hardware before the mainboard swap.

---

### Post by Ocxic on 2007-12-29
check to see if all of your current hardware is listed, it's possible the unknown stuff is the hardware that you have removed

---

### Post by dasunst3r on 2007-12-29
It seems to me that Linux detects hardware on every single boot and loads up modules accordingly.  I remember changing the motherboard on my dual-boot Fedora Core 3 and Windows XP installation a few years ago, and I only had to reconfigure the graphics card before I'm back on my feet.  Needless to say, I was afraid of even thinking about booting into Windows.

---

### Post by nutz on 2007-12-29
I was thinking the same thing, could be the old hardware that is no longer there. So far the system works flawlessly so I think everything was detected correctly.

---

### Post by Yellow Pasque on 2007-12-30
what do you get with lspci? You may need to run sudo update-pciids if you have unknown devices, but that's more for aesthetics than anything.

---

### Post by nutz on 2007-12-30
```
nutz@NutZ:~$ sudo lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0f.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:11.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 053b (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
nutz@NutZ:~$ 

```

---

### Post by Yellow Pasque on 2007-12-30
Ok. Run:
```
sudo update-pciids
``` (with internet connection) and unless those devices are really new and not in Ubuntu's database, it should fill in the names.

---

### Post by nutz on 2007-12-30
```
nutz@NutZ:~$ sudo update-pciids
[sudo] password for nutz:
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  126k  100  126k    0     0  35879      0  0:00:03  0:00:03 --:--:--  311k
Done.
nutz@NutZ:~$ sudo lspci00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0f.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:11.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 053b (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
nutz@NutZ:~$ 

```

---

### Post by d4ny on 2007-12-30
I have the same issue with my new HP Pavilion DV2620CA laptop.  I installed a fresh copy of Ubuntu Gutsy (with the noapic option).  When I ran *lspci* I had many unknown devices.  I tried *sudo update-pciids* and that helped to detect the unknown USB devices.

**Before:**

```

xxxxxxx@xxxxxxxx:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

```

**After**

```

xxxxxxxxx@xxxxxxxx:~$ sudo update-pciids
[sudo] password for xxxxxxxx:
--17:41:10--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 129,133 (126K) [text/plain]

100%[====================================>] 129,133       66.00K/s             

17:41:13 (65.87 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [129133/129133]

Done.
xxxxxxxx@xxxxxxxx:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

```

But as you can see, I still get many Unknown devices... I sill have some issues with devices not working but that is off topic.

---

### Post by nutz on 2007-12-30
So what is the best way to clear up these unknown devices? Reinstall?

---

### Post by Yellow Pasque on 2007-12-30
> **nutz said:**
> So what is the best way to clear up these unknown devices? Reinstall?
No, just wait for them to be added to the Ubuntu database. I believe (don't quote me) they won't affect operation as long as Ubuntu knows what type of device it is and has a driver.

---

### Post by marx2k on 2008-01-05
Having the same issue here on a motherboard using the nForce 630A MCP chipset.

Trying to find a fix as we speak. I would like to know if these pciids are going to be added into the next installment of Ubuntu. Does anyone know?

---

