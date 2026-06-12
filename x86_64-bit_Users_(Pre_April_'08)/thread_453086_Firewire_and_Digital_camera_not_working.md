---
title: "Firewire and Digital camera not working"
date: 2007-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by JKoder on 2007-05-24
Hello. I use Ubuntu 7.04 x64. I have a JVC camera that i used on ubuntu 6.10 before. Everything worked just fine. Now i tryed on Ubuntu 7.04 x64 and in dmesg i get a message something like:
NOTICE: /dev/dv1394 will soon be removed from Linux. Use instead /dev/raw1394.
and it tells me that tha camera vas mounted.

Using Kino i could not find my camera and i could not capture from it.
Does anyone have an ideea ?
Thank you

---

### Post by shad0w_walker on 2007-05-24
What device is kino trying to access your DV cam from?

Edit -> Preferences -> IEEE 1394

The dv1394 Device line should show something along the lines of:

```
/dev/dv1394
```

---

### Post by JKoder on 2007-05-24
on my place the DV device shows something like /dev/dv1394/0

---

### Post by shad0w_walker on 2007-05-24
Mine is pointing to exactly the same location. Have you tried pointing it at /dev/raw1394 ? My camera works fine for some reason, but doesnt work on raw1394, maybe yours is the opposite for whatever reason.

---

