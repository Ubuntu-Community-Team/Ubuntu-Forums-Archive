---
title: "USB flash drive not working on 64-bit kernels"
date: 2006-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by gwi on 2006-07-14
I have a Sandisk Cruzer U3 flash drive, 1GB. I used the U3 uninstaller to remove the U3 crap, so now it is just a plain USB flash drive. Using fdisk I removed the existing partition, and created a new one, and formatted it as FAT32 (mkfs.vfat -F 32).

I booted the installed AMD64-k8 kernel (2.6.15-26-amd64-k8): the USB flash drive was not recognised.
I booted the AMD64 live cd: the USB flash drive was not recognised.
I booted the i386 live cd: the USB flash drive worked properly.
I booted Windows XP Pro SP2: the USB flash drive worked properly.

So it seems only the 64-bit kernels have a problem. I have tried dozens of times, but the flash drive was only (partly) recognised two or three times. Is this a timing problem?

When I plug in the drive and do a lsusb or cat /proc/bus/usb/devices, nothing happens. The shell does nothing, no prompt. It just echoes what I type. Ctrl-C or ctrl-D don't work. Alt-F4 does close the window, but that's it.

lspci shows (among others):
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)

tail -f /var/log/syslog showed nothing when plugging in the flash drive.

Almost looks like the USB system has stopped running, but my USB connected Wacom Graphire still works.

Any ideas what is going on here, and why the problem only occurs on 64-bit kernels?
Did someone experience the same problems?

My motherboard is an Asus A8N SLI DeLuxe (nForce4 chipset), with an Athlon64-3200+ and 3GB RAM.

---

### Post by Teroedni on 2006-07-14
Try with theese 2 command 



```
sudo mkdir /media/usbdisk
```



```
sudo mount -t vfat /dev/sdb1 /media/usbdisk
```

the last command depend of what hardrive you have

---

### Post by gwi on 2006-07-15
> **Teroedni said:**
> 
```
sudo mount -t vfat /dev/sdb1 /media/usbdisk
```


Result: device does not exist (tried with /dev/sdf1)

When I booted the 32-bit live cd, the USB flash drive was assigned /dev/sdf1. When booted with a 64-bit kernel, there is only /dev/sda*, the partitions on my harddisk, no sdb, sdc or whatever.
lsusb does not show the device:
```

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 056a:0010 Wacom Co., Ltd Graphire
Bus 001 Device 003: ID 056d:0002 EIZO Corp.
Bus 001 Device 001: ID 0000:0000

```

where the 32-bit session showed:
```

[B]Bus 002 Device 008: ID 0781:5406 SanDisk Corp.
Bus 002 Device 004: ID 0dda:2027 Integrated Circuit Solution, Inc.[/B]
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 056a:0010 Wacom Co., Ltd Graphire
Bus 001 Device 003: ID 056d:0002 EIZO Corp.
Bus 001 Device 001: ID 0000:0000

```

In 32-bit the command cat /proc/bus/usb/devices showed (among others):
```

T:  Bus=02 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=5406 Rev= 0.10
S:  Manufacturer=SanDisk Corporation
S:  Product=U3 Cruzer Micro
S:  SerialNumber=0000060326111586
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=125us

```

In 64-bit this device is not shown. It looks like it is just not there. What I don't get is the difference in results between 32-bit and 64-bit Ubuntu.

---

### Post by walkerx on 2006-07-15
USB Flash Drives do work in 64bit version of Ubuntu

I think it depends on how they were formatted, if it gets detected properly

my travelmate 256mb is working fine, but this is formatted as fat32
my external hard-drive which is in an icy box, and has 2 primary partitions also works, these are formatted to ntfs (so no write access)

my nokia n80 used as flash drive is not recognised

as you can see from cat /proc/bus/usb/devices the usb storage devices are listed and also shows you the kernel i'm using which is 64bit

```
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  2, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-amd64-k8 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0605 Rev= 6.0b
S:  Product=USB2.0 Hub
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms

T:  Bus=03 Lev=02 Prnt=03 Port=00 Cnt=01 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=09a6 ProdID=8001 Rev= 1.00
S:  Manufacturer=Generic
S:  Product=USB Flash Disk
S:  SerialNumber=20030318183241-01
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms

T:  Bus=03 Lev=02 Prnt=03 Port=02 Cnt=02 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2001 ProdID=3c00 Rev= 0.01
S:  Manufacturer=ANI
S:  Product=802.11g W
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=300mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtusb
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms

T:  Bus=03 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=14aa ProdID=0221 Rev= 5.21
S:  Manufacturer=Digital TV Receiver
S:  Product=Digital TV Receiver
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=450mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=00 Driver=dvb_usb_dtt200u
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=86(I) Atr=03(Int.) MxPS=  64 Ivl=64ms

T:  Bus=03 Lev=01 Prnt=01 Port=05 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04b4 ProdID=6830 Rev= 0.01
S:  Manufacturer=Cypress Semiconductor
S:  Product=USB2.0 Storage Device
S:  SerialNumber=DEF107679C83
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-amd64-k8 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
B:  Alloc= 28/900 us ( 3%), #Int=  2, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-26-amd64-k8 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c50b Rev=21.00
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr= 98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
```

---

### Post by hajk on 2006-07-15
No problem with my latest USB stick either. It came with a small "floppy"-sized partition with Windows-based security software (U3 stuff?), that I removed by reformatting with an ext2 FS. I also reformatted the main partition as ext2. When I insert the stick, it shows two mounted partitions, /dev/sdb1 and /dev/sdb2.

Come to think of it, the partitions must be of type 83 (Linux), and can then be (re)formatted with the FS of choice, like vfat of ext2.

---

### Post by gwi on 2006-07-16
I tried again. This time after plugging in syslog showed:
```

Jul 16 20:48:14 saturnus kernel: [  478.549194] scsi5 : SCSI emulation for USB M *** Storage devices
Jul 16 20:48:14 saturnus kernel: [  478.549420] usb-storage: device found at 8
Jul 16 20:48:14 saturnus kernel: [  478.549422] usb-storage: waiting for device to settle before scanning
Jul 16 20:48:14 saturnus kernel: [  478.549584] usbcore: registered new driver usb-storage
Jul 16 20:48:14 saturnus kernel: [  478.549667] USB Mass Storage support registered.
Jul 16 20:48:18 saturnus kernel: [  481.048603]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 2.15
Jul 16 20:48:18 saturnus kernel: [  481.048612]   Type:   Direct-Access              ANSI SCSI revision: 02
Jul 16 20:48:22 saturnus udevd-event[6375]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:02.1/usb2/2-5/2-5:1.0/host5/target5:0:0/5:0:0:0/bus' failed

```

Does anyone know what can cause the failure of wait_for_sysfs?

There is no /dev/sd* other than the partitions on my SATA disk (/dev/sda*). Can the failure of wait_for_sysfs be caused by the partition format? I gave it type c (W95 FAT32 LBA), and formatted it with mkfs.vfat -F 32, so the filesystem should be readable (it is, when I boot a 32-bit kernel).
If I change it to a type 83, formatted as FAT32, will Windows be able to access it? (I do have to use it on both Linux and Windows, that's why I use FAT32.)

---

### Post by hajk on 2006-07-16
> **gwi said:**
> 
Does anyone know what can cause the failure of wait_for_sysfs?

There is no /dev/sd* other than the partitions on my SATA disk (/dev/sda*). Can the failure of wait_for_sysfs be caused by the partition format? I gave it type c (W95 FAT32 LBA), and formatted it with mkfs.vfat -F 32, so the filesystem should be readable (it is, when I boot a 32-bit kernel).
If I change it to a type 83, formatted as FAT32, will Windows be able to access it? (I do have to use it on both Linux and Windows, that's why I use FAT32.)

Yes, give it type 83 (Linux), then reformat the partition with 
"sudo mkfs.vfat -F FAT32 /dev/sdbx" where the device should match your actual device.

---

### Post by gwi on 2006-07-17
> **hajk said:**
> Yes, give it type 83 (Linux), then reformat the partition with 
"sudo mkfs.vfat -F FAT32 /dev/sdbx" where the device should match your actual device.

I did that (on another 32-bit computer). Windows still recognises it, 32-bit Ubuntu recognises it, but 64-bit Ubuntu still doesn't!

There is no /dev/sd* (except my harddisk /dev/sda), so nothing to use mount, fdisk or mkfs against.

---

### Post by hajk on 2006-07-17
Strange, I formatted my USB-key some time ago on my 32-bit Breezy (amd-k7), and I find that it is read fine by my current 64-bit amd-k8 setup... The only real difference I notice from your situation is that I didn't use the U3 uninstaller... of course I ended up with two partitions (one very small).
Could you perhaps try and first remove all partitions using cfdisk, then make new ones, etc?

---

### Post by gwi on 2006-07-18
I already did that (twice to be exact). First time I created a new partition, and gave it type c (Windows 95 FAT32 LBA), and formatted is as vfat FAT32. The second time I created a new partition and gave it type 83 (Linux). This one I also formatted as FAT32.
In both cases I used fdisk not cdisk, but that should not be important.
I first thought it could be a problem with my setup of the amd64-k8 kernel, but booting the amd64-generic kernel from the live cd produces the same results. So a complete reinstall would probably not change anything.

---

### Post by gwi on 2006-07-20
Just began to wonder why the USB flash drive problem started around the same time I expanded RAM to 3GB. I now have 2x 512MB and 2x 1024MB RAM.

I tried it with just 2x 512MB: no problem.
With 2x 1024MB: no problem.
With 2x 1024MB and 2x 512 MB (reversed the order): problem is back.

I tried to search google, on terms like Ubuntu 3GB, but it returns results handling 3GB disks or partitions.

Does anyone know of problems related to running a 64-bit kernel on a computer with 3GB RAM?

---

### Post by Teroedni on 2006-07-21
> **gwi said:**
> Just began to wonder why the USB flash drive problem started around the same time I expanded RAM to 3GB. I now have 2x 512MB and 2x 1024MB RAM.

I tried it with just 2x 512MB: no problem.
With 2x 1024MB: no problem.
With 2x 1024MB and 2x 512 MB (reversed the order): problem is back.

I tried to search google, on terms like Ubuntu 3GB, but it returns results handling 3GB disks or partitions.

Does anyone know of problems related to running a 64-bit kernel on a computer with 3GB RAM?

First are you sure your motherboard supports 2x512 and 2sx1024 at the same time
Does bios shows it as 3gb?

---

### Post by gwi on 2006-07-22
> **Teroedni said:**
> First are you sure your motherboard supports 2x512 and 2sx1024 at the same time
Does bios shows it as 3gb?

Yes it does (although they note that for performance it is better to have 4 modules of the same size). The bios shows 3GB.

---

### Post by olivierp on 2006-07-22
> **gwi said:**
> Just began to wonder why the USB flash drive problem started around the same time I expanded RAM to 3GB. I now have 2x 512MB and 2x 1024MB RAM.

I tried it with just 2x 512MB: no problem.
With 2x 1024MB: no problem.
With 2x 1024MB and 2x 512 MB (reversed the order): problem is back.

I tried to search google, on terms like Ubuntu 3GB, but it returns results handling 3GB disks or partitions.

Does anyone know of problems related to running a 64-bit kernel on a computer with 3GB RAM?

Found this on google: [http://linux.derkeiler.com/Mailing-Lists/Kernel/2005-07/2135.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2005-07/2135.html)

It seems like a kernel/usb issue. You may be able to get your key working, but at USB 1.1 speeds.

I would report this in malone ([https://launchpad.net/malone](https://launchpad.net/malone)) against your current kernel package. You could also try the usb-dev mailing lists, or the kernel mailing list. This doesn't seem to be distribution specific.

---

### Post by lox_federico on 2006-07-23
I have an ASUS A8N-E Mainboard with a AMD Athlon64 X2 4800+ CPU, I experienced the same problem, here's how I solved it:

open a terminal and run:

```
sudo modprobe -r ehci_hcd
```

wait a couple of seconds then run:

```
sudo modprobe ehci_hcd
```

Now plug your usb storage device and see if it works (for me it does after running those commands), if it works let's run this one at session startup:

```
sudo gedit /usr/bin/enableusb2.sh
```

paste this:

```
modprobe -r ehci_hcd
sleep 2
modprobe ehci_hcd
```

now let's add this to sudoers:

```
sudo visudo
```

append this line at the end of file:

```
%yourusername ALL=NOPASSWD: /usr/bin/enableusb2.sh
```

Now go to System > Preferences > Sessions, click on the last tab ("Programs startup", I'm not sure since I'm running Ubuntu in Italian language), click Add and put this command in the dialog:

```
sudo enableusb2.sh
```

Now your USB2.0 ports will work at startup and will do it at full speed.

---

### Post by gwi on 2006-07-24
> **lox_federico said:**
> I have an ASUS A8N-E Mainboard with a AMD Athlon64 X2 4800+ CPU, I experienced the same problem, here's how I solved it:
...


I have an Asus A8N SLI DeLuxe with an AMD Athlon64 3200+.

> 
Now your USB2.0 ports will work at startup and will do it at full speed.

Unfortunately they don't. I did modprobe -r ehci_hcd, after a few seconds followed by modprobe ehci_hcd. I then plugged in the USB flash disk. The system (at least the PS/2 keyboard and USB Wacom Graphire) froze completely.

After a reboot I tried again. I did modprobe -r ehci_hcd, waited ca. 10 seconds. This time the system froze directly after I did the modprobe ehci_hcd, even before I plugged in the flash drive.

Maybe I will use another workaround until the problem is solved: remove the 2x 512MB, and run with the 2x 1024MB. Should be enough for now anyway.

---

### Post by jamaas on 2006-07-29
I'm having the same trouble with regular 32 bit ubuntu  on a notebook and n80!  Can you answer quickly for a newbie ... is there a way to fix this, read something about a kernel patch but not sure I can compile new kernel.  Will this ever get fixed in regular kernels from ubuntu?  

My regular 128 mb sd disk works fine, but new 2 gig one not recognized!

Thanks

Jim

my nokia n80 used as flash drive is not recognised

as you can see from cat /proc/bus/usb/devices the usb storage devices are listed and also shows you the kernel i'm using which is 64bit

[

---

