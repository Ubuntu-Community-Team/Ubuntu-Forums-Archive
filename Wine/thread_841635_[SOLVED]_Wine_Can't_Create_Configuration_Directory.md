---
title: "[SOLVED] Wine Can't Create Configuration Directory"
date: 2008-06-26
forum: Wine
---

### Post by bren21 on 2008-06-26
I just installed wine and did the winecfg, but for some reason I am getting an error saying that it can't create the directory in home. Here's the error message
```

$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
wine: creating configuration directory '/home/brendan/.wine'...
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Could not load Mozilla. HTML rendering will be disabled.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Segmentation fault
wine: wineprefixcreate failed while creating '/home/brendan/.wine'.
```

Anyone know whats wrong?

---

### Post by cogadh on 2008-06-26
Fix those preloader errors:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

What version of Wine are you using?

---

### Post by mc4man on 2008-06-26
You may (or anyone else installing on hardy) go here, add the wine repo and get the latest rc version.
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
It's somewhat surprising the hardy repo continues to use an unsuitable version -  0.9.59. vs. one of the rc releases
Technically it could be viewed as a security update. Quote from preloader fix page
> This fixes the problem until the next time you reboot. (It also reduces security slightly.)  

---

### Post by bren21 on 2008-06-26
The preloader fix did not work, it just gave me a different error. But when I added the repo and installed the new version it worked perfectly. Thanks for the help guys.

---

