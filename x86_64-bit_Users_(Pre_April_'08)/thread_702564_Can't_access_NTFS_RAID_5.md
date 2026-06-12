---
title: "Can't access NTFS RAID 5"
date: 2008-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by getsome831 on 2008-02-20
Getting this message below while trying to access my RAID5 (NTFS) drive.  Using a [[COLOR="Blue"]Cavalry RAID[/COLOR]]("http://www.cavalrystorage.com/CADA002SA4.asp").  Drive works great under winXP, no joy in ubuntu so far though.

[ATTACH]60452[/ATTACH]

$MFT has invalid magic.  Failed to load $MFT:Input/output error Failed to mount '/dev/sda1':Input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware.  In the first case run chkdsk /f on Windows then reboot into Windows TWICE.  The usage of the /f parameter is very important!  If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details.

Sorry for the utter lack of detail, i will be able to provide the make/model of the raid card and/or mobo or anything else log wise you probably need to help once i get back in front of the machine after work.  Any thoughts in the meantime though?

---

### Post by fjgaude on 2008-02-20
Unless you have a driver for the card that is designed to load into Ubuntu you will have to consider other ways, like using dmraid. Such can only be used after you have installed Ubuntu on a drive. Then you will likely be able to get, by using dmraid and gaining much understanding, Ubuntu to recognize your raid setup.

Let us know how you are doing.

---

### Post by getsome831 on 2008-02-20
I have a Sil3132...i got this after i ran the following...

> sudo update-pciids
sudo lspci

gregg@gregg-desktop:~$ sudo lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)
[COLOR="Red"]02:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)[/COLOR]
05:06.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
05:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

And yet i still can't access the volume, am i missing something.  I see 64 drivers here ([http://www.siliconimage.com/support/supportsearchresults.aspx?pid=32&cid=3&ctid=2&osid=2&](http://www.siliconimage.com/support/supportsearchresults.aspx?pid=32&cid=3&ctid=2&osid=2&)) but nothing for ubuntu.  Yet in this [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=379267") it sounds like it should work...how do i "load the drivers from the kernel"?  Maybe i should just ask the poster in the other thread though...

Thanks again.

---

### Post by fjgaude on 2008-02-21
Well, you have to get the RPM driver from wherever, then convert it to DEB. Then install it into your running Ubuntu system.

I don't know anything more about the drivers for SIL raid.

The other way, and here again I'm not sure Linux handles raid5 yet, is to use the dmraid feature. Such will permit you to see and mount a raid volume while Ubuntu is running. Using ntfs-3g you can read and write to the volume. If you are interesting in trying this method I can help here. I did this some years ago and it worked good.

Let us know what you do, and how you are doing.

---

### Post by getsome831 on 2008-03-03
Any tips on converting an RPM to DEB?

---

### Post by fjgaude on 2008-03-03
Yes, there is a program that does the comversion, but for the life of me I can't think of its name.

Maybe someone else can.

---

### Post by 655 on 2008-05-13
The package is called Alien.

---

