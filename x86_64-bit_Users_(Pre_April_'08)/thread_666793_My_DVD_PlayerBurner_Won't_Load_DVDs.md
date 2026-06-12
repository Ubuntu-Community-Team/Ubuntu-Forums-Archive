---
title: "My DVD Player/Burner Won't Load DVDs"
date: 2008-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mark76 on 2008-01-13
I've tried over a dozen and I get nothing. The green light flashes.  I can hear the disc spinning and then...

Nothing.

The computer is pretty much brand new as well (Compaq SR5219), so I refuse to believe the DVD drive has crapped out.

---

### Post by santaslittlehelper on 2008-01-13
Hi

Might be helpful if you posted the output of,
```
cat /etc/fstab
```

You could also try to pop in a DVD, then from terminal,
```
sudo mount -a
```
See if it produces any errors.

Is it all disks, data as well?
Maybe you just need libdvdcss.

---

