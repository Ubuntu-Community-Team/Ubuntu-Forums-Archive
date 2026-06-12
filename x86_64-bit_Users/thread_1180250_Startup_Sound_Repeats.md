---
title: "Startup Sound Repeats"
date: 2009-06-06
forum: x86 64-bit Users
---

### Post by amtur_poet on 2009-06-06
I just installed Ubuntu 9.04 64-bit via Wubi on my HP Pavillion dv7, but whenever I start my system, the startup "drum" sound constantly repeats, and won't stop. What should I do to fix this?

---

### Post by amtur_poet on 2009-06-09
isn't there any way to fix this? It's really annoying.

---

### Post by BladeOfAnduril on 2009-06-14
I have this exact same problem.  Anyone???  I'd love to get this fixed.

---

### Post by rtalcott on 2009-06-14
I have the same problem...and other than the repeating drum I can get no sound.
rt

---

### Post by yage on 2009-06-14
Here's what to do;
edit alsa base.conf
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
Put this in the end of the file
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```
Save, and close gedit.

Reboot!

---

### Post by yage on 2009-06-14
This is useful for HP users!
[howto-ubuntu-linux-on-hp-pavilion-dv-series-laptops]("http://http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops")

---

### Post by BladeOfAnduril on 2009-06-30
It worked!! Thank you!!!!

---

