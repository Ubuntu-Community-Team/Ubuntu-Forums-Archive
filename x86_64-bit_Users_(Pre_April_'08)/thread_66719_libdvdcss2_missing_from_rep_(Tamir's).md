---
title: "libdvdcss2 missing from rep (Tamir's)"
date: 2005-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by acariquara on 2005-09-18
Actually, it shows up at the apt list but fails to download (404)

> W: Falha ao obter [http://tamir.nooms.de/ubuntu/dists/hoary/universe/binary-amd64/libdvdcss2_1.2.9-1ubuntu1_amd64.deb](http://tamir.nooms.de/ubuntu/dists/hoary/universe/binary-amd64/libdvdcss2_1.2.9-1ubuntu1_amd64.deb)
  404 Not Found


---

### Post by jensyt on 2005-09-18
He probably removed the package (for legal reasons) without updating the Packages.gz file...

At least, that's what I think it could be.

---

### Post by mlomker on 2005-09-18
Yes he did.  I'm not sure why he hasn't updated his package list.

This one works:

```

deb ftp://ftp.nerim.net/debian-marillat unstable main

```

---

### Post by Corbelius on 2005-09-18
[QUOTE=acariquara]Actually, it shows up at the apt list but fails to download (404)[/QUOTE]

I made that package, if u want it contact me on email: [http://tamir.nooms.de/wiki/doku.php?id=about](http://tamir.nooms.de/wiki/doku.php?id=about)

---

### Post by ibthomson on 2005-09-19
You can run a script already included instead of downloading the package.
```

sudo apt-get install fakeroot
sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh
```

Works just fine.

---

