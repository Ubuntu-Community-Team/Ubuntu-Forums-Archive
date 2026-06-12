---
title: "Google earth wont install on amd-64?"
date: 2007-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by notna01 on 2007-09-14
```

anton@anton-desktop:~/Desktop$ sudo sh ./google.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.180.1134..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
anton@anton-desktop:~/Desktop$ 

```
That is what i get..... I am running beryl if that is any help...
Please help me.

---

### Post by serendib on 2007-09-15
Painless way that I did was to install Automatix and then install the 32-bit Google Earth, which is in the "Office" packages of Automatix.

---

### Post by marco123 on 2007-09-15
Definitely turn Beryl off, it should install then.
Also be careful when running Google Earth with Beryl running as well; the only time I've had Ubuntu freeze up on me(had to do a hard reboot) was when I tried to maximize Google Earth while running Beryl.:(

---

