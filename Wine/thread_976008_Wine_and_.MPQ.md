---
title: "Wine and .MPQ"
date: 2008-11-08
forum: Wine
---

### Post by Bofur on 2008-11-08
I'm trying to install wow with one of the more recent dvd's out there and there is no installer.exe on it. It has Installer Tome.mpq, Installer Tome 2.mpq etc etc. When I try to open with wine via Terminal I get this output:

```
justin@ubuntu:~/Desktop/WoW$ wine "Installer Tome.mpq"
wine: could not load L"Z:\\home\\justin\\Desktop\\WoW\\Installer Tome.mpq": Bad EXE format for 
justin@ubuntu:~/Desktop/WoW$ 

```

Not really sure what to do from here. Any help would be appreciated! And yes, I copied all the files from the cd to my desktop. Thanks!

---

### Post by Bofur on 2008-11-09
Fixed it, had to edit my etc/fstab and add unhide to the line. :popcorn:

---

