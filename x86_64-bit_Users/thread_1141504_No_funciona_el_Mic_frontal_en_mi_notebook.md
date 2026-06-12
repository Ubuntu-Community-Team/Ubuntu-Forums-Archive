---
title: "No funciona el Mic frontal en mi notebook"
date: 2009-04-28
forum: x86 64-bit Users
---

### Post by maxid on 2009-04-28
Instale sobre una DV5-1235dx Ubuntu 8.10 64bits y no logro que grabe sonidos con el mic frontal.
Si abro alsamixer en la captura no figura el mic. Y desde las preferencias se sonido el mic aparece mudo, lo habilito  cierro vuelvo a entrar y aparece de nuevo mudo.

esto devuelven los lshw y lspci

**sudo lshw -short**

H/W path         Device      Class       Description
====================================================
                             system      HP Pavilion dv5 Notebook PC
/0                           bus         3603
/0/0                         memory      1MiB BIOS
/0/e                         processor   Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
/0/e/f                       memory      3MiB L2 cache
/0/e/11                      memory      32KiB L1 cache
/0/e/1.1                     processor   Logical CPU
/0/e/1.2                     processor   Logical CPU
/0/10                        memory      32KiB L1 cache
/0/12                        memory      4GiB System Memory
/0/12/0                      memory      2GiB SODIMM Synchronous 800 MHz (1.2 ns)
/0/12/1                      memory      2GiB SODIMM Synchronous 800 MHz (1.2 ns)
/0/100                       bridge      Mobile 4 Series Chipset Memory Controller Hub
/0/100/1                     bridge      Mobile 4 Series Chipset PCI Express Graphics Port
/0/100/1/0                   display     GeForce 9200M GS
/0/100/1a                    bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                  bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.7                  bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                    multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                    bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c/0      eth1        network     BCM4312 802.11b/g
/0/100/1c.1                  bridge      82801I (ICH9 Family) PCI Express Port 2
/0/100/1c.1/0    eth0        network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1c.2                  bridge      82801I (ICH9 Family) PCI Express Port 3
/0/100/1c.3                  bridge      82801I (ICH9 Family) PCI Express Port 4
/0/100/1c.4                  bridge      82801I (ICH9 Family) PCI Express Port 5
/0/100/1c.4/0                bus         IEEE 1394 Host Controller
/0/100/1c.4/0.1              system      SD/MMC Host Controller
/0/100/1c.4/0.2              system      Standard SD Host Controller
/0/100/1c.4/0.3              system      MS Host Controller
/0/100/1c.4/0.4              system      xD Host Controller
/0/100/1c.5                  bridge      82801I (ICH9 Family) PCI Express Port 6
/0/100/1d                    bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                  bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                  bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.3                  bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1d.7                  bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                    bridge      82801 Mobile PCI Bridge
/0/100/1f                    bridge      ICH9M LPC Interface Controller
/0/100/1f.2      scsi0       storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0    /dev/sda    disk        320GB WDC WD3200BEVT-6
/0/100/1f.2/0/1  /dev/sda1   volume      289GiB Windows NTFS volume
/0/100/1f.2/0/2  /dev/sda2   volume      9080MiB Windows NTFS volume
/0/100/1f.2/1    /dev/cdrom  disk        DVD RW AD-7561S
/0/100/1f.2/1/0  /dev/cdrom  disk        
/0/100/1f.3                  bus         82801I (ICH9 Family) SMBus Controller
/0/100/1f.6                  generic     82801I (ICH9 Family) Thermal Subsystem
/1               pan0        network     Ethernet interface

**sudo lspci**

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

---

### Post by itxaka on 2009-04-28
I got the same issue and the best thing was to update alsa using the script here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

After that I had to make ubuntu load some modules, but those are maily to get sound over HDMI.

Update alsa with the script and reboot.

Also, check on Volume control if you have checked "input source" and change them on the options tab from "Mic" to "frontal mic"


Cheers.

---

### Post by maxid on 2009-04-28
I will try later, tell you tomorrow
Thanks

---

