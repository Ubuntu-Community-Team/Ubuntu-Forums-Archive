---
title: "Please insert the correct CD-ROM error for Black and White 2"
date: 2012-02-12
forum: Wine
---

### Post by acornty on 2012-02-12
Right then! here's my story. I used to play black and white 2 a lot back in the days when I had windows vista running on the computer I'm typing this from. Now I have Ubuntu 11.10 on it and I had the sudden urge to play BW2 again. Unfortunately I've lost the discs. I "obtained" some .iso's and installed the game. I ran into absolutely no problems except when I try to start it and I get the error. I have the Disc_1 iso mounted and have used wincfg to tell wine to look for the mount point, yet I still get this error. I've tried about a million different mounting applications and techniques and get the same error. I've also tried installing the game with playonlinix and still get the error. Is there anyway to get this game working? I miss being a god :(

Thanks! 
Tyler

EDIT: Just found out how to enable dubugging mode in playonlinix. This is the output

```
[POL_Wine] Message: Running wine- white.exe
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 41018 (device=4 access=0 func=406 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 24804 (device=2 access=1 func=201 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 24804 (device=2 access=1 func=201 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 24804 (device=2 access=1 func=201 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 24804 (device=2 access=1 func=201 method=0)
```

---

