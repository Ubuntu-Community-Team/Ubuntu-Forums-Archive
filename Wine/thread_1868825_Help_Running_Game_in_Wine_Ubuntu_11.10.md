---
title: "Help Running Game in Wine Ubuntu 11.10"
date: 2011-10-24
forum: Wine
---

### Post by TurtleKing on 2011-10-24
Use to be able to get the game to run smoothly in Ubuntu 10.10. In 11.04 and 11.10 I cannot get passed the Launch/Title screen. It changes resolution, and loads up for the next screen only to crash. In wine1.2, I get a pop-up saying "debugger is running, and to unload it." For Wine1.3 I am able to at least get the Title/Launch Screen to show up.

Here is the terminal output of running the game in wine1.3:
```
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 70020 (device=7 access=0 func=8 method=0)
fixme:win:EnumDisplayDevicesW ((null),0,0x32f8ac,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
err:alsa:ALSA_CheckSetVolume Could not find '{PCM,Line} Playback Volume' element
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x337a6c8,0x337129c): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x3371468,0x337129c): stub
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x65b567
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x62e408,0x64a72a): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x00000060,0x130e20,0x64a72a): stub
err:eventlog:ReportEventW L"6"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null)," "): stub
fixme:advapi:RegisterEventSourceW (L"",L" "): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x62e408,0x64a7ba): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000000,(nil),0x0001,0x000002cc,0x130e20,0x64a7ba): stub
err:eventlog:ReportEventW L"7"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
name@computer:$

```

Any idea why the game does not work? It does not seem to be a problem with the game since I have not done anything to it from Ubuntu 10.10 to Ubuntu 11.10.

---

### Post by TurtleKing on 2011-10-29
bump.

---

### Post by ergo-proxy on 2011-10-30
> **TurtleKing said:**
>  It does not seem to be a problem with the game since I have not done anything to it from Ubuntu 10.10 to Ubuntu 11.10.

Except from wine version which changes every two weeks unless you usethe stable one.

---

### Post by TurtleKing on 2011-10-31
So the stable wine version now crashes, and the new wine version works but crashes. Definitely making progress here.

/sarcasm

---

### Post by Tweak42 on 2011-11-03
Are you running wow from a ntfs partition?  Did you try from a clean WINEPREFIX or did you keep reusing the one from 10.10?  Which version of wine1.3 have you experience these errors?  What video hardware and driver version are you using?  Clean install of 11.10 or upgrade?

---

### Post by TurtleKing on 2012-03-31
Wow I'm happy to say things have gone for the better. Tried to install popular MMORPG F2P game, Rusty Heart. And the game runs all the way to patching itself. Sadly, the patch is 809 MB so I had cancel it. Here is to hoping that Forsaken World will be able to run as well (Best Free MMORPG in my book).:D

---

