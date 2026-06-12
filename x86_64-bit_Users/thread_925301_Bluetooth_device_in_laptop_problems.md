---
title: "Bluetooth device in laptop problems"
date: 2008-09-20
forum: x86 64-bit Users
---

### Post by matthiasak on 2008-09-20
I have a brand new Dell Inspiron 1318 and have had Hardy x86_64 rnning for about a week and a half... Bluetooth was working earlier, but for some reason now it is not and I have no idea why, I have not modified any startup services, etc, and I have everything else working, only installed some software (Skype, Opera, inkscape, etc...)



I've searched around and can't find anything that has actually helped me yet.

I can find the device with dmesg, but I can't in lsusb or lspci... gnome bluetooth manager and the bluetooth thread startup on system boot..

uname -r:

```
matthiasak@matthiasak-laptop:~$ uname -r
2.6.24-19-generic

```

dmesg | greb 'Bluetooth' :

```
matthiasak@matthiasak-laptop:~$ dmesg | grep 'Bluetooth'
[   31.945398] Bluetooth: Core ver 2.11
[   31.945695] Bluetooth: HCI device and connection manager initialized
[   31.945699] Bluetooth: HCI socket layer initialized
[   31.976446] Bluetooth: L2CAP ver 2.9
[   31.976449] Bluetooth: L2CAP socket layer initialized
[   31.998173] Bluetooth: RFCOMM socket layer initialized
[   31.998184] Bluetooth: RFCOMM TTY layer initialized
[   31.998185] Bluetooth: RFCOMM ver 1.8

```

lsusb: 

```
matthiasak@matthiasak-laptop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 
```

lspci:

```
matthiasak@matthiasak-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```


help :(

---

