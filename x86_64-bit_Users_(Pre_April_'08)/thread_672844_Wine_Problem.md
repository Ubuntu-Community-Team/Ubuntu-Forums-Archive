---
title: "Wine Problem"
date: 2008-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by masoodkamal on 2008-01-20
i have AMD 64

i installed wine and then tried to run "BIOSHOCK"
i got the following message


masood@masood-desktop:~$ wine /media/sda12/bioshock3/builds/release/bioshock.exewine: creating configuration directory '/home/masood/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/masood/.wine'.
masood@masood-desktop:~$ wineserver: could not save registry branch to /home/masood/.wine-D86nKD/system.reg : No such file or directory
wineserver: could not save registry branch to /home/masood/.wine-D86nKD/user.reg : No such file or directory


Please help :(

---

### Post by Yellow Pasque on 2008-01-20
What method did you use to install wine and what version are you using?
Also, run the winecfg program and configure your setup. This should create the .wine directory for you in your home folder.

---

### Post by bharadwaj on 2008-01-20
are other apps able to run successfully?

---

### Post by whatever on 2008-01-20
> **masoodkamal said:**
> i installed wine and then tried to run "BIOSHOCK"

bioshock does not (yet) work with wine: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5695](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5695)

---

