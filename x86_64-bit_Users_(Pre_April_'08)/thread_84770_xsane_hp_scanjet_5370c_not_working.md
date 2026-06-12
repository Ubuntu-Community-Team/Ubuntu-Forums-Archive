---
title: "xsane hp scanjet 5370c not working"
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by mealot on 2005-10-31
root@ubuntu:/# sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x03f0 [Hewlett Packard], product=0x0701 [Hewlett Packard ScanJet 5300C/5370C ]) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

root@ubuntu:/# scanimage -L
device `avision:libusb:001:003' is a Hewlett-Packard ScanJet 5370C flatbed scanner

My scanner info is all correct in /etc/bus/devices as well but it pops up with the scanner search icon in GUI and then nothing happens when I use xsane, I have also tried kooka and it detects nothing.  I cant seem to get a frontend to communicate with the backend that seems to see my scanner?

msi k8n neo 2 platinum
2 gb dual channel ram
x 800 xt platinum
audiology 2 platinum 
250 gb wd sata
250 gb ide maxtor
athlon 64 939 3500+
 any help would be helpful :)  I can't seem to find any other 64 distros that see all this equipment so I am stuck with Ubuntu :(

---

### Post by AllenGG on 2005-11-01
Hi, have used XSANE quite a lot.  On HP 1315 PSC, USB connect.
BUT............ hard to fool around to get it running, some settings, pref's are in various place. Took me  1 hour or so. Now it works fine. Also had to search for drivers within 5.10

Allen
(AMD64, K8V se Del, 1.5 G ram. 2 SATA HDD's)

---

### Post by mealot on 2005-11-01
could you possibly point me to a forum you used or something as such, since I have exhauseted all means I know how to do to get it working :)  thanks

---

### Post by mealot on 2005-11-01
(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 46912584672688 (LWP 8908)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00002aaaabee1ba4 in waitpid () from /lib/libc.so.6
#0  0x00002aaaabee1ba4 in waitpid () from /lib/libc.so.6
#1  0x00002aaaac81870d in KCrash::defaultCrashHandler ()
   from /usr/lib/libkdecore.so.4
#2  0x00002aaaabe81190 in killpg () from /lib/libc.so.6
#3  0x0000000000000000 in ?? ()
#4  0x0000000000000000 in ?? ()
#5  0x0000000000000000 in ?? ()
#6  0x0000000200000002 in ?? ()
#7  0x0000000000000000 in ?? ()
#8  0xfefefefefefefeff in ?? ()
#9  0x0000000000000008 in ?? ()
#10 0x0000000000752790 in ?? ()
#11 0x0000000000753540 in ?? ()
#12 0x000000000084fb98 in ?? ()
#13 0x000000000084fb00 in ?? ()
#14 0x00000000008bf758 in ?? ()
#15 0x00007fffffbc3ee0 in ?? ()
#16 0x0000000100000000 in ?? ()
#17 0x0000000000000000 in ?? ()
#18 0x000000000000000c in ?? ()
#19 0x0000000000000006 in ?? ()
#20 0xfefefefeff716e6b in ?? ()
#21 0x0000000100000000 in ?? ()
#22 0x0000000000000000 in ?? ()
#23 0x00007fffffbc3e78 in ?? ()
#24 0x00002aaaabec2d40 in strlen () from /lib/libc.so.6
#25 0x0000000000010246 in ?? ()
#26 0x0000000000007bfe in ?? ()
#27 0x0000000000000004 in ?? ()
#28 0x000000000000000e in ?? ()
#29 0x0000000000000000 in ?? ()
#30 0x0000000100000000 in ?? ()
#31 0x00007fffffbc3bf0 in ?? ()
#32 0x00007fffffbc4370 in ?? ()
#33 0x0000000000764078 in ?? ()
#34 0x00000000008a5678 in ?? ()
#35 0x00000000008a5618 in ?? ()
#36 0x00002aaaabebbb36 in free () from /lib/libc.so.6
#37 0x00002aaaad0f05a7 in QGArray::deleteData () from /usr/lib/libqt-mt.so.3


I get this when i try kooka? Now

---

