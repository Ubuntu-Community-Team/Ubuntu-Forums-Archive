---
title: "Inserting any optical disk hard freezes computer"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by RobbieCrash on 2008-05-09
x86_64 hardy install, everything was working fine.

Tried to install w64 codecs in order to get encrypted dvd playback to work, now any time I insert a cd/dvd my system hard freezes. 

Music playback turns into a constant replaying of whatever half second of sound was playing at that moment. SSH sessions are dropped, the whole deal. No way to restart aside from hard reset or power button off. 

Nothing in syslog.

Any ideas?

---

### Post by tevaughan on 2008-07-08
I have seen the exact same problem.  Any help would be appreciated.

---

### Post by soxs on 2008-07-08
post the line of your /etc/fstab where it says /media/cdrom or /media/cdrom0

and post where an inserted disc is mounted (and the /dev/* where the cd actually is, you can obtain that from "mount" (type it into a terminal))

---

