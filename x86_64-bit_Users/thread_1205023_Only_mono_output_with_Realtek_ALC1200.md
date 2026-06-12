---
title: "Only mono output with Realtek ALC1200"
date: 2009-07-05
forum: x86 64-bit Users
---

### Post by gunslinger3 on 2009-07-05
Running 9.04 64 bit on an HP desktop. 

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC1200

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

the startup music sounds stereo but anything after that (music and movies) only play in mono.

new to Linux but love what I see

---

### Post by gunslinger3 on 2009-07-05
Never mind. Rebooted and stereo is there :)

---

