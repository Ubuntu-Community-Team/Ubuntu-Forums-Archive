---
title: "Cannot launch Adept"
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by obsrv on 2008-08-22
I get this error while launching adept:

```
obsrv@obsrv-laptop:~$ sudo adept_manager
[sudo] password for obsrv:
kapture::PkgSystem::PkgSystem()
Error: "/var/tmp/kdecache-obsrv" is owned by uid 1000 instead of uid 0.
adduser
debconf
sysklogd
snort-mysql
oinkmaster
adduser
debconf
sysklogd
snort-mysql
oinkmaster
KCrash: Application 'adept_manager' crashing...
KCrash cannot reach kdeinit, launching directly.

```

What is wrong?

---

### Post by LateNiteTV on 2008-08-22
try:
```

chown root /path/to/adept_manager
```

---

