---
title: "Mathematica installation"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by elmoosecapitan on 2008-11-12
Hi,

Is there anyway to install a Mathematica iso file without burning to a CDROM first?

I have a legal copy with a license.

Best

---

### Post by bgs100 on 2008-11-12
Try this:
[https://help.ubuntu.com/community/Mathematica]("https://help.ubuntu.com/community/Mathematica")

Hope it helps!

---

### Post by jpkotta on 2008-11-13
```
sudo mount -o loop mathematica.iso /cdrom
sudo sh /cdrom/Unix/Installer
```

---

