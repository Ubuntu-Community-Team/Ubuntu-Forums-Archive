---
title: "USB subsystem crash after USB disk connected"
date: 2008-08-02
forum: x86 64-bit Users
---

### Post by Doc on 2008-08-02
Hi,

This morning on my Hardy amd64 system, after plugging in a harddrive in an external enclosure to attempt to back up some files I found I suddenly couldn't use my USB mouse or keyboard. Luckily I had a spare ps/2 keyboard I was able to plug in to gracefully restart the system. Here is the output of /var/log/kern.log:

<---disk connected--->

Aug  2 11:15:16 jhs kernel: [26562.774159] scsi 7:0:0:0: Direct-Access     ST332062 0AS                   PQ: 0 ANSI: 2 CCS
Aug  2 11:15:16 jhs kernel: [26562.774698] sd 7:0:0:0: [sdg] 625142448 512-byte hardware sectors (320073 MB)
Aug  2 11:15:16 jhs kernel: [26562.789341] sd 7:0:0:0: [sdg] Write Protect is off
Aug  2 11:15:16 jhs kernel: [26562.789345] sd 7:0:0:0: [sdg] Mode Sense: 00 38 00 00
Aug  2 11:15:16 jhs kernel: [26562.789346] sd 7:0:0:0: [sdg] Assuming drive cache: write through
Aug  2 11:15:16 jhs kernel: [26562.789694] sd 7:0:0:0: [sdg] 625142448 512-byte hardware sectors (320073 MB)
Aug  2 11:15:16 jhs kernel: [26562.789926] sd 7:0:0:0: [sdg] Write Protect is off
Aug  2 11:15:16 jhs kernel: [26562.789928] sd 7:0:0:0: [sdg] Mode Sense: 00 38 00 00
Aug  2 11:15:16 jhs kernel: [26562.789930] sd 7:0:0:0: [sdg] Assuming drive cache: write through
Aug  2 11:15:16 jhs kernel: [26562.789932]  sdg: sdg1 sdg2
Aug  2 11:15:16 jhs kernel: [26562.800760] sd 7:0:0:0: [sdg] Attached SCSI disk
Aug  2 11:15:16 jhs kernel: [26562.800787] sd 7:0:0:0: Attached scsi generic sg6 type 0
Aug  2 11:15:17 jhs kernel: [26563.250927] ReiserFS: sdg1: found reiserfs format "3.6" with standard journal
Aug  2 11:15:17 jhs kernel: [26563.250936] ReiserFS: sdg1: using ordered data mode
Aug  2 11:15:17 jhs kernel: [26563.257170] ReiserFS: sdg1: journal params: device sdg1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
Aug  2 11:15:17 jhs kernel: [26563.257955] ReiserFS: sdg1: checking transaction log (sdg1)
Aug  2 11:15:17 jhs kernel: [26563.303876] ReiserFS: sdg1: Using r5 hash to sort names
Aug  2 11:15:17 jhs kernel: [26563.759992] usb 6-3.1: reset full speed USB device using ehci_hcd and address 7

<---here's where I disconnected/reconnected my USB mouse/keyboard to get them working again--->

Aug  2 11:17:50 jhs kernel: [26616.380716] usb 6-4: USB disconnect, address 4
Aug  2 11:17:50 jhs kernel: [26616.380720] usb 6-4.1: USB disconnect, address 6
Aug  2 11:18:04 jhs kernel: [26620.544455] usb 6-4: new high speed USB device using ehci_hcd and address 9
Aug  2 11:18:19 jhs kernel: [26625.273198] usb 6-4: device descriptor read/64, error -110
Aug  2 11:18:34 jhs kernel: [26630.034562] usb 6-4: device descriptor read/64, error -110
Aug  2 11:18:34 jhs kernel: [26630.101993] usb 6-4: new high speed USB device using ehci_hcd and address 10
Aug  2 11:18:49 jhs kernel: [26634.831044] usb 6-4: device descriptor read/64, error -110
Aug  2 11:19:05 jhs kernel: [26639.592253] usb 6-4: device descriptor read/64, error -110
Aug  2 11:19:05 jhs kernel: [26639.659681] usb 6-4: new high speed USB device using ehci_hcd and address 11
Aug  2 11:19:15 jhs kernel: [26642.916494] usb 6-4: device not accepting address 11, error -110
Aug  2 11:19:15 jhs kernel: [26642.951464] usb 6-4: new high speed USB device using ehci_hcd and address 12
Aug  2 11:19:26 jhs kernel: [26646.207965] usb 6-4: device not accepting address 12, error -110

<---here's where I disconnected the USB disk--->

Aug  2 11:19:26 jhs kernel: [26646.207983] usb 6-3: USB disconnect, address 3
Aug  2 11:19:26 jhs kernel: [26646.207985] usb 6-3.1: USB disconnect, address 7
Aug  2 11:19:26 jhs kernel: [26646.306767] usb 6-3: new high speed USB device using ehci_hcd and address 13
Aug  2 11:19:41 jhs kernel: [26651.035669] usb 6-3: device descriptor read/64, error -110
Aug  2 11:19:57 jhs kernel: [26655.796879] usb 6-3: device descriptor read/64, error -110
Aug  2 11:19:57 jhs kernel: [26655.864311] usb 6-3: new high speed USB device using ehci_hcd and address 14
Aug  2 11:20:12 jhs kernel: [26660.593212] usb 6-3: device descriptor read/64, error -110

<---here's where I (hotplugged!) the ps/2 keyboard--->

Aug  2 11:20:25 jhs kernel: [26664.613820] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input8
Aug  2 11:20:27 jhs kernel: [26665.354577] usb 6-3: device descriptor read/64, error -110
Aug  2 11:20:27 jhs kernel: [26665.422162] usb 6-3: new high speed USB device using ehci_hcd and address 15
Aug  2 11:20:38 jhs kernel: [26668.678666] usb 6-3: device not accepting address 15, error -110
Aug  2 11:20:38 jhs kernel: [26668.713786] usb 6-3: new high speed USB device using ehci_hcd and address 16
Aug  2 11:20:48 jhs kernel: [26671.970292] usb 6-3: device not accepting address 16, error -110

Neither of the USB keyboard or mouse worked again until I restarted. Anybody have any ideas what's going on here?

Thanks for any replies
hs

---

### Post by Doc on 2008-08-02
An update:  this problem is definitely reproducible, and I think I was looking at the wrong logfile. I should have been looking at /var/log/syslog:

Aug  2 11:20:48 jhs kernel: [26671.970567] Buffer I/O error on device sdg1, logical block 5252
Aug  2 11:20:48 jhs kernel: [26671.970570] lost page write due to I/O error on sdg1
Aug  2 11:20:48 jhs kernel: [26671.970572] Buffer I/O error on device sdg1, logical block 5253
Aug  2 11:20:48 jhs kernel: [26671.970573] lost page write due to I/O error on sdg1
Aug  2 11:20:48 jhs kernel: [26671.970637] REISERFS: abort (device sdg1): Journal write error in flush_commit_list
Aug  2 11:20:48 jhs kernel: [26671.970639] REISERFS: Aborting journal for filesystem on sdg1
Aug  2 11:20:48 jhs kernel: [26672.005562] ReiserFS: sdg1: warning: zam-7001: io error in reiserfs_find_entry
Aug  2 11:20:48 jhs kernel: [26672.012148] ReiserFS: sdg1: warning: zam-7001: io error in reiserfs_find_entry
Aug  2 11:20:48 jhs kernel: [26672.012300] ReiserFS: sdg1: warning: zam-7001: io error in reiserfs_find_entry
Aug  2 11:20:48 jhs hald[10018]: forcibly attempting to lazy unmount /dev/sdg1 as enclosing drive was disconnected
Aug  2 11:20:48 jhs kernel: [26672.014170] ReiserFS: sdg1: warning: zam-7001: io error in reiserfs_find_entry
Aug  2 11:20:48 jhs kernel: [26672.024225] ReiserFS: sdg1: warning: zam-7001: io error in reiserfs_find_entry
Aug  2 11:20:49 jhs hald: unmounted /dev/sdg1 from '/media/disk' on behalf of uid 0
Aug  2 11:20:49 jhs kernel: [26672.068588] Buffer I/O error on device sdg1, logical block 5255
Aug  2 11:20:49 jhs kernel: [26672.068592] lost page write due to I/O error on sdg1
Aug  2 11:20:49 jhs kernel: [26672.068594] Buffer I/O error on device sdg1, logical block 5256
Aug  2 11:20:49 jhs kernel: [26672.068595] lost page write due to I/O error on sdg1
Aug  2 11:21:07 jhs kernel: [26679.407767] usb 6-3: new high speed USB device using ehci_hcd and address 17
Aug  2 11:21:23 jhs kernel: [26684.136828] usb 6-3: device descriptor read/64, error -110 

But should a (USB) disk read error take out other USB devices?

---

### Post by Doc on 2008-08-02
Running reiserfsck:

reiserfsck 3.6.19 (2003 [www.namesys.com](www.namesys.com))

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to [email]reiserfs-list@namesys.com[/email], **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  [www.namesys.com/support.html](www.namesys.com/support.html). **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sdg1
Will put log info to '/home/jhs/Desktop/sdg1.log'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
###########
reiserfsck --check started at Sat Aug  2 13:23:17 2008
###########
Replaying journal..
Reiserfs journal '/dev/sdg1' in blocks [18..8211]: 0 transactions replayed

The problem has occurred looks like a hardware problem. If you have
bad blocks, we advise you to get a new hard drive, because once you
get one bad block  that the disk  drive internals  cannot hide from
your sight,the chances of getting more are generally said to become
much higher  (precise statistics are unknown to us), and  this disk
drive is probably not expensive enough  for you to you to risk your
time and  data on it.  If you don't want to follow that follow that
advice then  if you have just a few bad blocks,  try writing to the
bad blocks  and see if the drive remaps  the bad blocks (that means
it takes a block  it has  in reserve  and allocates  it for use for
of that block number).  If it cannot remap the block,  use badblock
option (-B) with  reiserfs utils to handle this block correctly.

bread: Cannot read the block (44236800): (Input/output error).

<---end--->

Obviously a hardware problem. Sad because this harddisk is barely a year old.

Maybe I should call up Namesys to help out. I wonder if the phone rings to Hans Reiser's cell block? 

hs

---

### Post by Doc on 2008-08-03
Ok, so as it turns out there's more to it than just a bad block on a harddisk. I plugged in my epson scanner this AM and turned it on and the same thing happens, my other USB devices stop working. I should mention that things worked fine on Gutsty, but during the upgrade to Hardy I took the opportunity to upgrade some hardware, including my mainboard, a Gigabyte AMD64 S-Series. 

The same output is in syslog:

Aug  2 11:18:04 jhs kernel: [26620.544455] usb 6-4: new high speed USB device using ehci_hcd and address 9
Aug  2 11:18:19 jhs kernel: [26625.273198] usb 6-4: device descriptor read/64, error -110
Aug  2 11:18:34 jhs kernel: [26630.034562] usb 6-4: device descriptor read/64, error -110
Aug  2 11:18:34 jhs kernel: [26630.101993] usb 6-4: new high speed USB device using ehci_hcd and address 10
Aug  2 11:18:49 jhs kernel: [26634.831044] usb 6-4: device descriptor read/64, error -110
Aug  2 11:19:05 jhs kernel: [26639.592253] usb 6-4: device descriptor read/64, error -110
Aug  2 11:19:05 jhs kernel: [26639.659681] usb 6-4: new high speed USB device using ehci_hcd and address 11
Aug  2 11:19:15 jhs kernel: [26642.916494] usb 6-4: device not accepting address 11, error -110
Aug  2 11:19:15 jhs kernel: [26642.951464] usb 6-4: new high speed USB device using ehci_hcd and address 12
Aug  2 11:19:26 jhs kernel: [26646.207965] usb 6-4: device not accepting address 12, error -110
Aug  2 11:19:26 jhs kernel: [26646.207983] usb 6-3: USB disconnect, address 3

So it's not the device, its a kernel level USB issue or my USB bus is flaky.  Anyone have any suggestions on debugging?

hs

---

### Post by Doc on 2008-09-25
I think I have finally tracked this down. It was reproducible with different SATA disks, at least the freezing of my USB keyboard/mouse and the same log errors. The problem was with the external enclosure, an 'Icy Box' manufactured by RaidSonic. I found their FAQ that implies that only fat32 filesystems are supported on their devices! Here is the link to the offending device: 

[http://www.raidsonic.de/en/pages/products/external_cases.php?we_objectID=5236]("http://www.raidsonic.de/en/pages/products/external_cases.php?we_objectID=5236")

I don't know if this is the problem or if there is a kernel bug, but until it is ever determined I suggest avoiding this vendor at all costs.

hs

---

### Post by Doc on 2008-09-26
Ok, so I got a response from the manufacturer and they insist the device supports all filesystems; the documentation I read was ambiguous. It looks like others have had issues with slowdowns and freezing of other USB devices, though with a different error number. I'll post this to linux-usb-devel.

hs

---

