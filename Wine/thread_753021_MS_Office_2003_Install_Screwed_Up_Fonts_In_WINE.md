---
title: "MS Office 2003 Install Screwed Up Fonts In WINE"
date: 2008-04-12
forum: Wine
---

### Post by bitznbytes on 2008-04-12
Hi,
I'm running Ubuntu and I installed Wine fine. From there I installed Photoshop 7 fine. All was working well until I tried to install Office 2003. It installed but would not run and would always crash.....that was fine.....so I tried to uninstall it using the wine uninstaller...and it will not uninstall......ALSO.....everytime I run photoshop now, it uses a weird small script font for everything! So I tried to uninstall WINE and re-install photohop but I am still getting a weird SCRIPT FONT everytime I try and run anything in WINE now......can anyone shed some light on this for me????

Thanks,
B

---

### Post by lswest on 2008-04-12
sounds like your preferences were messed up, try going into nautilus hitting ctrl+h to view hidden folders, go to the folder .wine, and then delete the three text files you see there (system.reg, user.reg, userdef.reg) and then opening a terminal and typing ```
winecfg
``` to re-create those files.  If that doesn't work, try uninstalling wine, deleting the whole .wine folder, and starting over.

---

### Post by bitznbytes on 2008-04-13
thanks that worked...just deleted the entire directory....do you know if any ver of ms office will work with wine?

---

