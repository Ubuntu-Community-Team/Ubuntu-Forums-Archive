---
title: "Installed App. Icons not showing"
date: 2009-07-03
forum: x86 64-bit Users
---

### Post by bcarney on 2009-07-03
I just installed 9.04 64 bit on an MSI VR705 laptop. The standard apps and icons were installed without any issues. I've started adding additional apps  but just noticed that most of the app icons are not available in the applications menus (games menu for instance). Package manager show the packages were isntalled and I did not locate any errors. Is there an issue with installing apps on 9.04 64bit? There used to be a command that you could run that would rebuild the icons and menus in Mandrake. Is there a simular command for Ubuntu (I've been away from linux for awhile).

Thanks in advance 
Brian

---

### Post by techstop on 2009-07-03
> **bcarney said:**
> There used to be a command that you could run that would rebuild the icons and menus in Mandrake. Is there a simular command for Ubuntu (I've been away from linux for awhile).

Thanks in advance 
Brian

```
killall gnome-panel
```

...will refresh your menus. 

If they still don't show up, go to Preferences>Main Menu. You may need to tick new entries so they show up. 

Finally, if the entries aren't there at all, you will need to add them (but they almost certainly will be if you've just installed packages from the ubuntu repository).

---

