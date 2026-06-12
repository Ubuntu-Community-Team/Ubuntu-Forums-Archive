---
title: "External drive not mounting"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by eruheru on 2008-05-06
Hey all, I just started dual booting hardy heron. My external hard drive (Simple Tech 320gb) won't mount. I had a similar issue with Mandriva, where it would only mount as "read-only" Does any one know how to fix this?
thanks

---

### Post by bpl07 on 2008-05-06
Install ntfs-config.  NTFS support is standard, but you need to configure it if you want to automount drives.  Make sure ntfs-3g is installed too, but it already should be.

---

### Post by saru411 on 2008-05-06
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

this site has solved any mounting issues that i've come across

---

### Post by half_life on 2008-07-17
Have you found an answer to this yet.  I have the same problem with the same drive on H.Heron 64bit.  I have to modprobe -r ehci_hcd to get it to see the drive.  This is way too slow for my needs.

Denny

---

