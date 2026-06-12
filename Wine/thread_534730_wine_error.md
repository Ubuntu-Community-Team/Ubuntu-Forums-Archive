---
title: "wine error"
date: 2007-08-25
forum: Wine
---

### Post by wog on 2007-08-25
I recently updated wine. Now when I try to use it I get this error:

wine client error:1f: version mismatch 307/309.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

I get this error if I attempt to access wine in any way, with any set of switches, or try to use 'winecfg'. I've tried uninstalling and reinstalling, and I still get this error.

Can anyone help?

---

### Post by cogadh on 2007-08-25
Try doing this when you uninstall it:
```
sudo apt-get remove --purge wine
```
That should remove all traces of the previous Wine install (except your .wine directory) and you should be able to reinstall it normally. If that doesn't work, try renaming your .wine directory then running winecfg to create a new one.

BTW - How did you originally install Wine (i.e. from the Ubuntu repositories, the Wine repositories or self compiled)?

---

### Post by wog on 2007-08-25
As it turned out I had to rename the old directory to start over. I can now do winecfg, so I assume I just reinstall my old games and all is well.

Originally, I installed from the repos and then from the winehq site with the wget command line they give you when I saw the latest version on winehq was newer than the version in the Ubuntu repos. 

I originally installed a long time ago, before the last dist-upgrade. This problem cropped up right after the most recent wine update, if it matters.

Thanks for the help! :)

---

