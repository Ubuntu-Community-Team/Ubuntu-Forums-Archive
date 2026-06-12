---
title: "Random Freezes"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by thekat on 2008-04-26
Anyone having random freezes.. ??
It just locks up a hard reset is all that fixes it..
It has happened 2 times on this install..
(All I was doing was listening to music and browsing not installing
anything at the time)

I was thinking memory because of this error
```

syslog.0:Apr 26 07:47:05 hardy64 kernel: [   19.771236] Your BIOS doesn't leave a aperture memory hole
syslog.0:Apr 26 07:47:05 hardy64 kernel: [   20.997002] Freeing initrd memory: 8205k freed
syslog.0:Apr 26 07:47:05 hardy64 kernel: [   21.947118] Freeing unused kernel memory: 316k freed


```

I ran MemTest on this box for hours yesterday with no errors..
So maybe a tweak somewhere..?

Edit:
Some more information..
```

20.128081] CPU 0: aperture @ 4000000 size 32 MB
[   20.128083] Aperture too small (32 MB)
[   20.137894] No AGP bridge found
[   20.137898] Your BIOS doesn't leave a aperture memory hole
[   20.137899] Please enable the IOMMU option in the BIOS setup
[   20.137901] This costs you 64 MB of RAM
[   20.162454] Mapping aperture over 65536 KB of RAM @ 4000000
[   20.224987] Memory: 8182612k/9175040k available (2466k kernel code, 204456k reserved, 1309k data, 316k init)
*
*
*
[   20.806566] PCI-DMA: Disabling AGP.
[   20.806758] PCI-DMA: aperture base @ 4000000 size 65536 KB
[   20.806762] PCI-DMA: using GART IOMMU.
[   20.806767] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture

```

Looks like Memory is Ok.. 

tk

---

### Post by Yahuda on 2008-04-26
I have the same problem. But, it freezes like ten times in an hour. Sometimes it doesn't freeze. I couldn't find any reason or solution.

---

### Post by thekat on 2008-04-27
Got some more info on this.. 
Yall might check your logs also..

```

ctran@hardy64:~$ grep fail /var/log/syslog
**After a lock up and reboot via the reset button**
Apr 27 06:56:31 hardy64 kernel: [   20.511394] 0000:00:13.1 OHCI: BIOS handoff failed (BIOS bug ?) 00000184
Apr 27 06:56:31 hardy64 kernel: [   26.790100] PM: Resume from disk failed.
**Just a reboot**
Apr 27 07:14:28 hardy64 kernel: [   27.431413] 0000:00:13.1 OHCI: BIOS handoff failed (BIOS bug ?) 00000184
Apr 27 07:14:28 hardy64 kernel: [   31.845074] PM: Resume from disk failed.


```
I am going to change out the disk later today and see if this goes away..

---

### Post by Cappy on 2008-04-27
The lines you are finding are possibly irrelevant to the freezing. If that IS the problem I don't think there is a solution. There is a way to check though: Pull out your RAM until you are left with 2gb and see if you still get freezes.

Diagnosing a system that freezes is difficult.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

If you get lucky, when your system freezes a SysRq+m will give an error message. In Gutsy I was having freezes and a few SysRq+m's later and I found out that it was a problem with the USB drivers.

Check the very bottom of the wiki page too, it shows you how to safely reboot even if X freezes.

---

### Post by thekat on 2008-04-27
I was scanning the logs for any indication..

I found smarttools
```

ctran@hardy64:~$ sudo  smartctl -d ata -a /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3200YS-01PGB0
Serial Number:    WD-WCAPD4161289
Firmware Version: 21.00M21
User Capacity:    320,072,933,376 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Apr 27 08:17:49 2008 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (9000) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 104) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   200   187   021    Pre-fail  Always       -       4958
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       29
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4391
 10 Spin_Retry_Count        0x0013   100   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0013   100   253   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       28
190 Temperature_Celsius     0x0022   070   040   000    Old_age   Always       -       30
194 Temperature_Celsius     0x0022   120   090   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

and I have run a diagnostic test.. 
I really don't think the drive is bad.. but was looking for 
symptoms..

Currently running a more extensive test.. Just to eliminate the
disk..
```
ctran@hardy64:~$ sudo smartctl -d ata -t long /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 104 minutes for test to complete.
Test will complete after Sun Apr 27 10:03:53 2008

Use smartctl -X to abort test.



```

---

### Post by thekat on 2008-04-28
> **Cappy said:**
> 

Diagnosing a system that freezes is difficult.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

If you get lucky, when your system freezes a SysRq+m will give an error message. In Gutsy I was having freezes and a few SysRq+m's later and I found out that it was a problem with the USB drivers.

Check the very bottom of the wiki page too, it shows you how to safely reboot even if X freezes.

Cappy.. 
Thx for the response.. 
I **think** the problem is related to FireFox.. (sqllite issue)
Preferences >Security > Deselected the "Tell me" boxes.. 

I used Epiphany yesterday.. No Freezing
Just trying FireFox again today.. so far so good... 

tk

---

### Post by Yahuda on 2008-05-01
[http://forum.compiz-fusion.org/showthread.php?t=8065](http://forum.compiz-fusion.org/showthread.php?t=8065)

---

### Post by Half-Left on 2008-05-01
Maybe seem obvious but have you guys updated your bios from your manufacturers website, that can fix alot of issues and graphics issues, even with the nvidia/ATI drivers.

---

### Post by millie95 on 2008-05-01
I had it happen once so far. I disabled the desktop effects after that. This feels like a bug in Ubuntu 8.04. I wouldn't update your BIOS or anything, wait for the fix

---

### Post by dpwilson on 2008-05-02
This happens to me a lot with 8.04.  Sometimes takes hours, and sometimes within minutes.  I have had compiz enable/disable, nvidia restricted driver and without.  If you read some of the other posts it affects a very wide range of hardware/software configs.  Hopefully someone will find a fix for it SOON!

---

### Post by AnotherFineMess on 2008-05-02
I had the same annoying glitches of high iowaits (constant Hard Disk use). I tried unistalling the Tracker Deamon, Fuse Server, disable Effects etc. but nothing seemed to actually make things better. I tried compiling the new kernel (2.6.25) though some it did not work 100% ok. In the end  i downloaded the kernel deb binaries from the Kernel archives for my AMD64 processor at [http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/]("http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/") which gave a breath of fresh air to my system. No more constant Hard Disk use...

[COLOR="Red"]You should uninstall your Graphics Card Drivers before rebooting and reinstall them after booting with your new kernel using the restricted drivers manager or with EnvyNG
[/COLOR]

Note that the correct files for the AMD64 architecture are:
[linux-headers-2.6.25-1-common_2.6.25-1snapshot.11177_amd64.deb]("http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/linux-headers-2.6.25-1-common_2.6.25-1snapshot.11177_amd64.deb")
[linux-image-2.6.25-1-amd64_2.6.25-1snapshot.11177_amd64.deb]("http://kernel-archive.buildserver.net/debian-kernel/pool/main/l/linux-2.6/linux-image-2.6.25-1-amd64_2.6.25-1snapshot.11177_amd64.deb")

When these 2 deb's are installed reboot and your new kernel will load as default from the grub menu

---

### Post by thekat on 2008-05-02
Yall..
Much thanks for all the replies.. 

I will chalk my problem up to FireFox Beta 5..

Since I disabled the check boxes I have 0 freezing..

oh..I have **not** installed the restricted drivers from
Nvidia.. 

I wanted to test the FireFox fix first.. so I can mark this 
one as solved ..

tk

---

### Post by alejandro.mc on 2008-05-03
Hey I tried going back to Firefox 2, disabling every effect in Compiz Fusion, Enabling or not the Restricted drivers, reinstalling gstreamer, and probably every other thing suggested at the moment in the web...

And it's still there..

I remember that with Gutsy I had to add "no apic" to the command line when i installed. Maybe i should have done tha same thing with Hardy? Or simply add it when I start Ubuntu? Would it fix something to do this? Could it be related to the problem? I've noticed that when this freezes occur (by the way the only thing to do when they occur it's to reset because nothing else works) the computer is working a lot and the fan is working at a very fast speed (sory I can't describe it better I'm not native english speaker)..

Thanks a lot in advance to everyone!

---

### Post by thekat on 2008-05-03
> **alejandro.mc said:**
> 

And it's still there..

I remember that with Gutsy I had to add "no apic" to the command line when i installed. Maybe i should have done tha same thing with Hardy? Or simply add it when I start Ubuntu? Would it fix something to do this? Could it be related to the problem? I've noticed that when this freezes occur (by the way the only thing to do when they occur it's to reset because nothing else works) the computer is working a lot and the fan is working at a very fast speed (sory I can't describe it better I'm not native english speaker)..

Thanks a lot in advance to everyone!

That is an option you could try ** no-acpi**

It depends on how old your MotherBoard / computer is.
If you have newer equipment like
- motherboard
- video card

It takes a while for the Linux to **catch up** to the hardware
sometimes..

In my case Gutsy would not even load on on my hardware - Hardy 
loaded and worked great.. so here I am .. :)

I don't have Compiz enabled so I am not using any Desktop
Effects.. 

Yes when my PC locks up it **totally freezes** 
- the screen 
- the mouse 
- the keyboard

Just like you have to push the reset button..

I did have one more freeze yesterday.. I was closing a video
on YouTube and the immediately switched to another Window..

Then I got a freeze just like before..

This confirms my belief that FireFox is the culprit... 

No worries on you English..   We can understand you ..:)

---

### Post by thekat on 2008-09-24
It has been a while.. about 3 months since I have been on forum..

UPDATE:

I just reloaded Hardy-64
- apt-get udate && apt-get upgrade (2 times)
no freezing..

What I found out.. 

There is a setting in the BIOS that needs to be enabled
to run 64-bit. 

Enabled this setting

**Power Management**
> 
ACPU XSDT Table
This table is for 64 bits OS using, Don't use for Win2k or WinXP 32 bits mode


Funny thing is that I found it on a Windows Forum when Vista 64-bit was
failing to install.. 

Symptoms 
Vista-64 would boot install and run the desktop for about 
30-60 seconds the shutdown
Rebooting it would hang right after BIOS 
with an 
ACPI Loader issue.

This might help someone else with a DFI board and more than 4 Gig of RAM
tk

---

### Post by ryclegman on 2008-12-05
Hello,

I have been working on this for a long time, and it seems to be a wireless driver issue.... I have a linksys pci and it randomly freezes when im downloading something from the internet.I don't think its GFX and definitely not memory issues. Linksys does not provide drivers for linux.. correct me if im wrong... The only way you can do it is that ntiswrapper, which i did get my driver installed, and it did find my hardware except it wouldn't connect to the internet :[..... i may try linux mint to see if that would work.... will let you know!

---

