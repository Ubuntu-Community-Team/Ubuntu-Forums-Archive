---
title: "32bit apps and network access"
date: 2008-05-16
forum: x86 64-bit Users
---

### Post by alloneword on 2008-05-16
Hello all.

I am trying to install a couple 32 bit apps, but I seem to have a strange issue. None of them can see my network. I tried install a 32 bit firefox (gave up), and now I just installed Google Earth, and it can also not connect to the net.

Any one come across this before?

Thanks for any help.

Tim.

P.S.
Ubuntu 8.04 64 bit.

---

### Post by Cappy on 2008-05-16
Try
```
sudo apt-get install lib32nss-mdns
```
from [http://ubuntuforums.org/showthread.php?t=763576](http://ubuntuforums.org/showthread.php?t=763576)

---

### Post by alloneword on 2008-05-16
> **Cappy said:**
> Try
```
sudo apt-get install lib32nss-mdns
```
from [http://ubuntuforums.org/showthread.php?t=763576](http://ubuntuforums.org/showthread.php?t=763576)

Thanks, worked a treat!!

---

