---
title: "Firewire disk issues"
date: 2006-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by sulobanks on 2006-01-10
I bought a La Cie 160 GB firewire hard disk. It works OS X just fine. Every time I plug it in, it shows up.  In Linux, sometimes it shows up, sometimes not. When it doesn't show up, it won't even show up in disk manager.  I can get it to show up most of the time if I boot up with it plugged in, but not always.  It shows up less than half the time when I plug it into a running system.  It would be nice not to have to reboot every time I decide to run a backup or every time I need to move my ibook.  Is firewire still just in it's infancy in Linux or is this supposed to work reliably?  I'm running breezy on a g4 ibook.

---

### Post by shawn12345 on 2006-01-10
I have the same problem, 2 lacie porsche drives

---

### Post by Focx on 2006-01-14
Same problem, 120gb, ibook g3... though it almost always shows up when I wait for 20 seconds after turning on the drive before turning on the ibook.

---

### Post by callipeo on 2006-01-14
Can you paste the output of dmesg after inserting the disk?

---

### Post by enupnia on 2006-01-16
same problem: witha a maxtor 250 Gb

the strange thing is that it works great under 5.04, but under 5.10 is NOT even regognized

---

### Post by enupnia on 2006-01-17
with dmesg i got this:

[  104.446767] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[  104.563993] sbp2: probe of 0010b9f700f50ec9-1 failed with error -16

---

