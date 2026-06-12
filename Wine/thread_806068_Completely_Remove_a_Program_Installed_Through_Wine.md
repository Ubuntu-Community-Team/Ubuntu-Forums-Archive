---
title: "Completely Remove a Program Installed Through Wine?"
date: 2008-05-24
forum: Wine
---

### Post by Kidfork on 2008-05-24
How do i uninstall a program i installed through wine. Everytime i try to Uninstall it just says its uninstalled then Its still there! In the registry and in the folder. I can still open it. So how can i completly take it off?

---

### Post by Kidfork on 2008-05-24
Im using Ubuntu 8.04 Hardy Heron and the Lastest Version of WINE

---

### Post by BlackDragonBE on 2008-05-24
I always do it manually, run the uninstall.exe or something like that and then edit your menu and remove the uninstalled application.

Cheers

---

### Post by Kidfork on 2008-05-24
Didn't Realy Work. Still didn't completely Uninstall It

---

### Post by cogadh on 2008-05-24
Delete the program directory, then go into Wine's registry and manually remove the uninstall entry for the program.

---

### Post by Kidfork on 2008-05-26
Yes,that just makes it so i cant open it, the actualy file is gone but its still in the wine directory.

---

### Post by inportb on 2008-05-26
Check to see if it's gone from .local/share/applications/wine/

---

### Post by cogadh on 2008-05-26
> **Kidfork said:**
> Yes,that just makes it so i cant open it, the actualy file is gone but its still in the wine directory.

Do you mean the Applications menu entry? If so, just go to System > Preferences > Main Menu and manually delete it. 

If you are referring to the program's installed files, when I said "delete the program directory", I meant delete the program's installed files found in ~/.wine/drive_c/Program Files (or whatever directory you installed it in).

---

