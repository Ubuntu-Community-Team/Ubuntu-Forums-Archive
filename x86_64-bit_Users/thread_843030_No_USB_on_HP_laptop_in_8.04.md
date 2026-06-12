---
title: "No USB on HP laptop in 8.04"
date: 2008-06-27
forum: x86 64-bit Users
---

### Post by Altur on 2008-06-27
I installed the x86 64-bit version of Ubuntu last week (had been using 32-bit) on my Hp pavillion laptop ([dv6604nr]("https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr)") for some information.) and I've loved it so far, pretty painless install and setup.  I have been using Ubuntu as my primary OS for about a year now, but am still not quite good enough to figure out some of this on my own.  I'm having issues getting any of my usb devices to work with my Laptop.  My mouse, keyboard, and printer will not work with the machine, nor any other usb devices I try to connect after the first 30 seconds after boot.  I don't know where to look to find any more information (error codes, outputs or anything).  If there's no solution I'll probably just reinstall, but I'd like to avoid that as I just got everything the way I like it.

I have tested my devices, and they all work in OpenSUSE 11, and with Vista.

On another, unrelated issue my nvidia graphics card is no longer supporting my 2nd monitor via TwinView, and if anyone knows a way to fix this, please let me know.

---

### Post by Altur on 2008-06-28
Tried reinstalling the system, no luck.

---

### Post by jimei on 2008-06-28
[Dunk SB]("http://www.gucci-sneaker.com/catalog_39.html")
[Air force one]("http://www.gucci-sneaker.com/catalog_42.html")

---

### Post by firecat53 on 2008-06-28
Try adding 'noapic irqfixup' to your grub boot parameters. I had to use those with my dv6058 laptop up through hardy. Don't need them anymore, but your hardware might be different.

Good luck!
Scott

---

### Post by Wizzykin on 2008-06-28
I'm having this issue trying to install Ubuntu Studio. Every time it loads the kernel and goes to the installation screen, my mouse and keyboard go out and I can't go any further. Driving me nuts.

---

### Post by mach9 on 2008-07-26
Did you ever find a solution to this problem?  I have a DV2000Z and installed 8.04 amd64 and have the same issue.  It was a clean install as well.
DMESG output
[   37.668926] usbcore: registered new interface driver usbfs
[   37.668952] usbcore: registered new interface driver hub
[   37.668979] usbcore: registered new device driver usb
[   37.721340] usb usb1: configuration #1 chosen from 1 choice
[   38.305107] usb 1-8: new high speed USB device using ehci_hcd and address 3
[   38.407233] usb usb2: configuration #1 chosen from 1 choice
[   38.428694] usb 1-8: device descriptor read/64, error -71
[   38.694149] usb 1-8: device descriptor read/64, error -71
[   38.924616] usb 1-8: new high speed USB device using ehci_hcd and address 4
[   39.048613] usb 1-8: device descriptor read/64, error -71
[   39.280575] usb 1-8: device descriptor read/64, error -71
[   39.508532] usb 1-8: new high speed USB device using ehci_hcd and address 5
[   39.920476] usb 1-8: device not accepting address 5, error -71
[   40.040463] usb 1-8: new high speed USB device using ehci_hcd and address 6
[   40.460402] usb 1-8: device not accepting address 6, error -71
[   40.784350] usb 2-4: new full speed USB device using ohci_hcd and address 2
[   41.018490] usb 2-4: configuration #1 chosen from 1 choice
[   52.486914] usbcore: registered new interface driver hci_usb
[   59.548872] usb 1-8: new high speed USB device using ehci_hcd and address 7
[   59.605299] usb 1-8: device descriptor read/64, error -71
[   59.728843] usb 1-8: device descriptor read/64, error -71
[   59.842842] usb 1-8: new high speed USB device using ehci_hcd and address 8
[   59.902842] usb 1-8: device descriptor read/64, error -71
[   60.014849] usb 1-8: device descriptor read/64, error -71
[   60.144240] usb 1-8: new high speed USB device using ehci_hcd and address 9
[   60.556215] usb 1-8: device not accepting address 9, error -71
[   60.676191] usb 1-8: new high speed USB device using ehci_hcd and address 10
[   61.092120] usb 1-8: device not accepting address 10, error -71

LSUSB output
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

LSPCI output
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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
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
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Any help would be appreciated as this is quite annoying.

As a extra note, NOTHING usb works or is recognized, though all devices function fine on other computers and worked previously under ubuntu.

---

