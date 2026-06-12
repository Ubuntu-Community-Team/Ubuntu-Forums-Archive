---
title: "webcam problem"
date: 2009-01-17
forum: x86 64-bit Users
---

### Post by pider55 on 2009-01-17
I got a new webcam for Xmas, Creative Live! Cam Video IM Pro and I cannot find any driver that will run with this. Anyone know a workaround or how to fix this?:) I run Ubuntu 8.10 64-bit.

---

### Post by cariboo on 2009-01-17
Are you sure the drivers for your device are not already installed. Install xawtv, it is available in the repositories, once it is installed open a terminal and type:

```
xawtv -c /dev/video0
```

You sould be able to see your self after doing the above. :)

Jim

---

### Post by pider55 on 2009-01-18
Installed xawtv and tried to run it, but this is what output Igot:
```
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-9-generic)
xinerama 0: 1440x900+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
```

---

