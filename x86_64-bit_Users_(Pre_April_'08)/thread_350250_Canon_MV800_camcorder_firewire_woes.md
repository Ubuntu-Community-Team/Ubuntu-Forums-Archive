---
title: "Canon MV800 camcorder firewire woes"
date: 2007-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by ziggykg on 2007-01-31
Hi,

I've been trying to get a Canon MV800 camcorder to work via firewire to no avail.  I'm running 64bit Edgy.  I've tried changing firewire cables (used a 4pin-4pin and a 4pin-6pin) just in case.

Interestingly, /dev/raw1394 modified's date gets updated each time I plug in the camcorder.

I've tried Kino (after setting /dev/raw1394 to readable and writable) but nothing's captured.  'dvgrab' isn't picking up the camera either.

I've loaded the various 1394 modules as directed by various posts.

Anyone got any ideas how I can solve this?

Cheers.

---

### Post by ziggykg on 2007-02-03
I solved my own problem by compiling and using kernel 2.6.19.2.  Camcorder now working with Kino and dvgrab.

---

### Post by changlinn on 2007-05-09
I thought a kernel update would fix my issues too, but Kino still doesn't detect my m800 neither does dmesg

Kino says dv1394 module not loaded or failure to write to /dev/raw1394

lsmod has the following
$ lsmod|grep 1394
dv1394                 20696  0 
video1394              19672  0 
raw1394                30328  0 
ohci1394               36528  2 dv1394,video1394
ieee1394              299448  4 dv1394,video1394,raw1394,ohci1394

modprobe has the following
$cat /etc/modprobe
lp
psmouse
ohci1394
ieee1394
raw1394
video1394
dv1394 <-- I only just added this though.

---

