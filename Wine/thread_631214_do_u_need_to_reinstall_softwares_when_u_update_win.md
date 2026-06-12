---
title: "do u need to reinstall softwares when u update wine?"
date: 2007-12-04
forum: Wine
---

### Post by sourcemorph on 2007-12-04
hey.. i have wine 0.9.46 n i wanna update it to 0.9.50 but i have a doubt .. does it require u to reinstall all softwares again??

i did a update to 0.9.49 a few days back by a .deb package frm getdeb.net n i then fifa 2008 won't start. so i uninstalled it n shifted back to 0.9.46 ... now i added the wine repository n my update manager shows thers an update available.. shud i do it?

---

### Post by Brynster on 2007-12-04
On the whole wine upgrades usually don't break things.

that said i have had issue's with wine when its been updated and broken my steam and half life installs.

best thing is to try it if it doesn't work then downgrade back to a version that does.

---

### Post by sourcemorph on 2007-12-04
ok thers this one more doubt... when i first downloaded wine frm add/remove programs... it downloaded something lke 35 mb of files... however the new version's .deb files r only 10-12 mb... do they miss something??

---

### Post by cogadh on 2007-12-04
When you first installed it, it probably also installed a couple of support packages (binfmt and libaudio) that are not necessarily reinstalled or redownloaded when updating the core Wine package. 

One thing that most people seem to forget: If you have made any manual registry edits in Wine, then after an update, you need to run "wineprefixcreate" in the terminal to re-register those registry changes. Other than that, Wine updates don't actually touch anything you have installed.

---

