---
title: "Burning problems"
date: 2009-03-13
forum: x86 64-bit Users
---

### Post by NarsilAnduril on 2009-03-13
Hi,

My DVD writer used to work fine with previous Ubuntu flavors (32 bits), but now that I've upgraded my motherboard to a 64 bits processor and installed 8.04 64 bits, it doesn't anymore.

Reads fine but can't burn. It does sometimes work with brasero (sometimes not), but K3b always fails to calibrate laser.

```
               *-cdrom
                   description: DVD writer
                   product: DVDRW SOHW-1653S
                   vendor: LITE-ON
                   physical id: 0.0.0
                   bus info: scsi@2:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/dvd
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: CS0T
                   capabilities: removable audio cd-r cd-rw dvd dvd-r
                   configuration: ansiversion=5 status=open
```

Does somebody know why ?

Thx

Diego

---

### Post by sanderj on 2009-03-14
Your post does not contain enough information.

I would do this: start k3b from the command line, then try to burn a CD, and post all command line output here in this forum (as CODE). Then search google for the errors / messages you see in k3b command line output.

HTH

---

### Post by NarsilAnduril on 2009-03-14
the command line output :

```
diego@Desktop:~$ k3b
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
kbuildsycoca running...
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
diego@Desktop:~$ (K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVDRW_SOHW_1653S to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
ICE default IO error handler doing an exit(), pid = 19713, errno = 11
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 2, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: CD Mastering
(K3bDevice::Device) /dev/scd0 feature: CD Track At Once
(K3bDevice::Device) /dev/scd0 feature: DVD+R
(K3bDevice::Device) /dev/scd0 feature: DVD+RW
(K3bDevice::Device) /dev/scd0 feature: DVD+R Double Layer
(K3bDevice::Device) /dev/scd0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/scd0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/scd0: dataLen: 60
(K3bDevice::Device) /dev/scd0: checking for TAO
(K3bDevice::Device) /dev/scd0: checking for SAO
(K3bDevice::Device) /dev/scd0: checking for SAO_R96P
(K3bDevice::Device) /dev/scd0: checking for SAO_R96R
(K3bDevice::Device) /dev/scd0: checking for RAW_R16
(K3bDevice::Device) /dev/scd0: checking for RAW_R96P
(K3bDevice::Device) /dev/scd0: checking for RAW_R96R
(K3bDevice::DeviceManager) setting current write speed of device /dev/scd0 to 8467
Could not resolve /dev/hdc
/dev/hdc resolved to /dev/hdc
(K3bDevice::Device) could not open device /dev/hdc for reading
                    (Aucun fichier ou dossier de ce type)
could not open device /dev/hdc (Aucun fichier ou dossier de ce type)
Could not resolve /dev/hdd
/dev/hdd resolved to /dev/hdd
(K3bDevice::Device) could not open device /dev/hdd for reading
                    (Aucun fichier ou dossier de ce type)
could not open device /dev/hdd (Aucun fichier ou dossier de ce type)
Could not resolve /dev/scd1
/dev/scd1 resolved to /dev/scd1
(K3bDevice::Device) could not open device /dev/scd1 for reading
                    (Aucun fichier ou dossier de ce type)
could not open device /dev/scd1 (Aucun fichier ou dossier de ce type)
/dev/scd0 resolved to /dev/scd0
(K3bDevice::DeviceManager) dev /dev/scd0 already found
(K3bDevice::DeviceManager) found config entry for devicetype: LITE-ON DVDRW SOHW-1653S
   0 - 01001111 - 79
   1 - 00111011 - 59
   2 - 01001010 - 74
/dev/scd0: ATIP capacity: 79:57:74
(K3bDevice::Device) READ CAPACITY: 25:35:10 other capacity: 79:57:74
DiskInfo:
Mediatype:       CD-R
Current Profile: CD-R
Disk state:      complete
Empty:           0
Rewritable:      0
Appendable:      0
Sessions:        1
Tracks:          1
Layers:          1
Capacity:        79:57:74 (LBA 359849) (736970752 Bytes)
Remaining size:  00:00:00 (LBA 0) (0 Bytes)
Used Size:       25:35:11 (LBA 115136) (235798528 Bytes)
Devices:
------------------------------
Blockdevice:    /dev/scd0
Generic device: 
Vendor:         LITE-ON
Description:    DVDRW SOHW-1653S
Version:        CS0T
Write speed:    8400
Profiles:       DVD-ROM, DVD-R séquentiel, DVD RW à réinscription limitée, DVD-RW séquentiel, DVD+RW, DVD+R, DVD+R double couche, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R séquentiel, DVD-RW, DVD RW à réinscription limitée, DVD-RW séquentiel, DVD+RW, DVD+R, DVD+R double couche, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R séquentiel, DVD-RW, DVD RW à réinscription limitée, DVD-RW séquentiel, DVD+RW, DVD+R, DVD+R double couche, CD-R, CD-RW
Writing modes:  SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Réinscription restreinte
Reader aliases: /dev/scd0
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
Session |  ADR   | CONTROL|  TNO   | POINT  |  Min   |  Sec   | Frame  |  Zero  |  PMIN  |  PSEC  | PFRAME |
      1 |      1 |      4 |      0 |     a0 |      0 |      0 |      0 |      0 |      1 |      0 |      0 |
      1 |      1 |      4 |      0 |     a1 |      0 |      0 |      0 |      0 |      1 |      0 |      0 |
      1 |      1 |      4 |      0 |     a2 |      0 |      0 |      0 |      0 |     25 |     37 |     11 |
      1 |      1 |      4 |      0 |      1 |      0 |      0 |      0 |      0 |      0 |      2 |      0 |
(K3bDevice::Device) found invalid bcd values. No bcd toc.
(K3bDevice::ScsiCommand) failed: 
                           command:    READ CD MSF (b9)
                           errorcode:  72
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       2
(K3bDevice::Device) /dev/scd0: READ CD MSF failed!
/dev/scd0: setting last sector of last track to 115135
(K3bDevice::Device) /dev/scd0:  Number of supported write speeds via 2A: 6
(K3bDevice::Device) /dev/scd0 : 8467 KB/s
(K3bDevice::Device) /dev/scd0 : 7056 KB/s
(K3bDevice::Device) /dev/scd0 : 5645 KB/s
(K3bDevice::Device) /dev/scd0 : 4234 KB/s
(K3bDevice::Device) /dev/scd0 : 2822 KB/s
(K3bDevice::Device) /dev/scd0 : 1411 KB/s
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  72
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       2
(K3bDevice::Device) /dev/scd0: READ 10 failed!
(K3bDevice::ScsiCommand) failed: 
                           command:    READ (10) (28)
                           errorcode:  72
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       2

```

k3b debug information

```
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-23-generic
Devices
-----------------------
LITE-ON DVDRW SOHW-1653S CS0T (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R séquentiel, DVD RW à réinscription limitée, DVD-RW séquentiel, DVD+RW, DVD+R, DVD+R double couche, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Réinscription restreinte]

K3bDataTrackReader
-----------------------
reading sectors 0 to 115135 with sector size 2048. Length: 115136 sectors, 235798528 bytes.
using buffer size of 64 blocks.
Read a total of 115136 sectors (235798528 bytes)

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identification : 'DVDRW SOHW-1653S'
Revision       : 'CS0T'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1895168 = 1850 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 8467 KB/s
Track 01: data   224 MB        
Total size:      258 MB (25:35.14) = 115136 sectors
Lout start:      258 MB (25:37/11) = 115136 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11607 (97:27/18)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 244713
Forcespeed is OFF.
Starting to write CD/DVD at speed  48.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 109.722s timeout 200s
/usr/bin/wodim: OPC failed.
Writing  time:  113.830s
/usr/bin/wodim: fifo had 191 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=48 -dao driveropts=burnfree -eject -data /tmp/sbs-ds4802.iso 


```

---

### Post by sanderj on 2009-03-14
"Errno: 5 (Input/output error), send opc scsi sendcmd: no error" *could* be interesting. [http://ubuntuforums.org/showthread.php?t=471181](http://ubuntuforums.org/showthread.php?t=471181) has something like that, but no solution.

Have you tried:
- updating your writer's firmware
- an other brand CD and DVD?

If that does not work either, and writing works ok in another Ubuntu version (32-bit version and/other release-version), you could report a bug on launchpad.

---

### Post by NarsilAnduril on 2009-03-14
- firmware is up to date
- it sometimes works, sometimes not, so it's hard to say if it's brand dependent
- it did work when my machine was running 32 bits (with another motherboard too, but that shouldn't matter)

Didn't find anything similar in launchpad, I'll post a new one.

Thx

Diego

---

### Post by sanderj on 2009-03-14
> **NarsilAnduril said:**
> 
- it did work when my machine was running 32 bits (with another motherboard too, but that shouldn't matter)

Didn't find anything similar in launchpad, I'll post a new one.


Another mobo could matter, actually; the disk controller is on your mobo.

So, maybe you could live-boot a 32-bit Ubuntu (from CD or USB stick), and see if you can still burn without problems.

---

### Post by NarsilAnduril on 2009-03-14
Good idea, i'll try that

---

### Post by Yellow Pasque on 2009-03-14
> - it did work when my machine was running 32 bits (with another motherboard too, but that shouldn't matter)
It could be due to your new motherboard's SATA settings. Do you have AHCI enabled?

---

### Post by SketchyClown on 2009-03-14
Check your motherboard BIOS for settings for the optical drive.

My optical drive would not work in Ubuntu 8.10 at all for reading or writing under the default BIOS settings.

I had to change the setting from "***Enhanced***" to "[I]**Compatible**".

[/I]Now the drive works flawlessly.

Check if your BIOS has a similar setting.

---

### Post by NarsilAnduril on 2009-03-15
> **sanderj]So, maybe you could live-boot a 32-bit Ubuntu (from CD or USB stick), and see if you can still burn without problems.[/QUOTE]

Same issue

[QUOTE=SketchyClown said:**
> I had to change the setting from "Enhanced" to "Compatible".

Didn't find anything like this

[QUOTE=Temüjin]It could be due to your new motherboard's SATA settings. Do you have AHCI enabled? [/QUOTE]

No idea what this is, I'll have to live ignoring it :rolleyes:, but it looks like changing this setting from "IDE" to "AHCI" _solved the problem_


Thank you very much

Diego

---

### Post by Yellow Pasque on 2009-03-15
> **NarsilAnduril said:**
> it looks like changing this setting from "IDE" to "AHCI" _solved the problem_
Thank you very much
You're welcome, Diego. Can you post the brand and model motherboard you have in case someone has the same issue and tries to search this forum or the web?

---

### Post by NarsilAnduril on 2009-03-16
Of course :

Motherboard type : ASUSTeK P5KC (Intel P35 Express)

---

