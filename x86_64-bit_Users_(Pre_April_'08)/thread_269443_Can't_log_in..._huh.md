---
title: "Can't log in... huh?"
date: 2006-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by except on 2006-10-01
Installed ubuntu amd64 edgy, worked reasonable, then changed the resolution to 1280x1024 via dpkg-reconfig xserver-xorg as someone else on the forum suggested, then rebooted, and now, when i log in, it just returns to the login screen... the resolution is higher though :)

---

### Post by kuja on 2006-10-01
Well, as an experiment, try creating a new user, and logging in as that user:

```

sudo adduser tester
su - tester
startx

```

Also, be sure to check Xorg's log (/var/log/Xorg.0.log) for errors.

---

