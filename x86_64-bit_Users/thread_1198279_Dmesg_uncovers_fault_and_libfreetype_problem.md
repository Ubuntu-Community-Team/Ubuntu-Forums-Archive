---
title: "Dmesg uncovers fault and libfreetype problem"
date: 2009-06-27
forum: x86 64-bit Users
---

### Post by afrodeity on 2009-06-27
I used dmesg for the first time trying to resolve an issue with my Via Chrome 9 driver and got a number of unrelated errors in addition to the info I needed about VIA. All of them appear to be something to do with Common Unix Printing system Cupsd and Freetype libraries, except for the "powertweakd" seg fault, 

```

[   83.268198] audit(1246094426.433:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6001 profile="/usr/sbin/cupsd" namespace="default"
[   84.068159] powertweakd[6057]: segfault at 6 rip 7f9d240e8060 rsp 7fff2cb36108 error 4
[   84.234509] audit(1246094427.401:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6077 profile="/usr/sbin/cupsd" namespace="default"
[   84.420164] audit(1246094427.590:4): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/usr/local/lib/libfreetype.so.6.3.20" pid=6097 profile="/usr/sbin/cupsd" namespace="default"
[   85.062837] audit(1246094428.233:5): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/usr/local/lib/libfreetype.so.6.3.20" pid=6098 profile="/usr/sbin/cupsd" namespace="default"

```

I would appreciate any help in resolving the above, because it might fix my libfreetype issues I have with WINE. I am in the process of googling, and will post if anything significant comes up, as you probably realise, Google relies a lot on the brains of the person googling, so I am still learning and observing.

---

