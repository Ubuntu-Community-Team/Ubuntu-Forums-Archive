---
title: "gnome hangs when I log-in for a second time"
date: 2007-12-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by coreSOLO on 2007-12-24
This may sound strange. When I start gnome for the first time everything works fine, but as soon as I log out and log in again (with the same user), desktop and panels does not load and disk access reaches 100%. Disk access does not after afterwards even if I wait for 30+ mins, if I log out, or even if I kill X. The only way to get rid of this is to restart my system. This has 100% reproducibility. Any idea whats wrong?

---

### Post by xelapond on 2007-12-24
Sounds like this might be a kernel or a hardware/driver error.  Please post your hardware specs and version of ubuntu.

Also, did you compile your own kernel?

---

### Post by coreSOLO on 2007-12-24
- nope I use stock kernel
- i cant be specific about software versions, but everything is updated to the latest
- using amd64 version
- thnx, I will check dmesg messages and post in case of any findings
- is there anything else I need to check apart from dmesg? like slog etc? i dont know anything other than dmesg so plz specify

also, I thing this issue night be related to nautilus as the whole desktop is not drawn and nautilus is used to draw it. just a wild guess, anyways, I will check dmesg and post back.

---

### Post by xelapond on 2007-12-24
Also try checking syslog to see if there is anything obvious.

Ar you running any proprietary drivers for graphics cards or anything?  Have you checked to make sure your hardware is compatible with Ubuntu?

You can check hardware compatibility here:  [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by coreSOLO on 2007-12-25
Okey! After turning "blick_dump" on, I fount that its Nautilus which is making insanely high number of disk writes. And this starts as soon as I log off (rather than logging in). So my question:

- is there any logoff/shutdown script associated with gnome/nautilus which runs on logging off? I might seach there for possible poblems.

PLz reply, this is very important.

---

