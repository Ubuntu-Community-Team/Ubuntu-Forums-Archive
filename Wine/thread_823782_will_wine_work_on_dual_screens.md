---
title: "will wine work on dual screens?"
date: 2008-06-09
forum: Wine
---

### Post by whitey on 2008-06-09
Hello,

I've been trying to get wine working on Xubuntu 7.10, and all I can seem to muster from it is the following:

whitey@reliant:~$ winecfg
wine: creating configuration directory '/home/whitey/.wine'...
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  145 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x199
  Serial number of failed request:  29
  Current serial number in output stream:  29
wine: wineprefixcreate failed while creating '/home/whitey/.wine'.
whitey@reliant:~$ wineserver: could not save registry branch to /home/whitey/.wine-bKPXxM/system.reg : No such file or directory
wineserver: could not save registry branch to /home/whitey/.wine-bKPXxM/user.reg : No such file or directory


I think the root of my issue might be that I'm running a dual screen setup of two nvidia cards and xinerama.  Wine is probably receiving a screen value larger than it is willing to handle "X Error of failed request:  BadWindow (invalid Window parameter)".

Anybody else running into this issue?

---

