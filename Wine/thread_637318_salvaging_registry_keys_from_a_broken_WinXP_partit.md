---
title: "salvaging registry keys from a broken WinXP partition"
date: 2007-12-10
forum: Wine
---

### Post by avismavis on 2007-12-10
my windows partition won't boot up and for the sake of discussion there's no way to fix it. i need some of the registry keys so that i can run a program in Wine. does anyone know how to read the files in windows\system32\config?

i can mount the partition and find the files, but when i can't figure out how to read them... all i need are the entries to run FL Studio 4.5 in Wine (which i can find myself if i can ever get this registry file open)

---

### Post by cogadh on 2007-12-10
Why not just run the install for the app in Wine so that the registry keys will be written to the Wine registry normally?

If that is not an options, this may help:
[http://osdir.com/ml/security.forensics/2006-04/msg00003.html?rfp=dta](http://osdir.com/ml/security.forensics/2006-04/msg00003.html?rfp=dta)

---

### Post by avismavis on 2007-12-11
whoaaa thanks i found dumphive here:
[http://v4.guadalinex.org/guadalinex-toro/pool/main/d/dumphive/](http://v4.guadalinex.org/guadalinex-toro/pool/main/d/dumphive/)

it took a lot of searching through system restore snapshots but i got the key i was looking for. thanks!!

---

