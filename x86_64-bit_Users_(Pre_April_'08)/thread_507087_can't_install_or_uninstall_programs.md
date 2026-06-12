---
title: "can't install or uninstall programs"
date: 2007-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by elquer on 2007-07-22
hi, i tried installing limewire but the package install froze so i forcequit the install before it was complete. now i have this error when i try to either install or delete applications from both the add remove applications and synaptic package manager. this is the error 


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


please someone help because this is keeping me from completing my linux customization. 

i'm using ubuntu feisty on a amd64, everything runs smooth up till now.

---

### Post by Sqwishy on 2007-07-22
Did you try running " dpkg --configure -a " in the terminal?

---

### Post by elquer on 2007-07-22
i dont' know how to, help please.

---

### Post by forestpixie on 2007-07-22
open a terminal - accessories> terminal

enter

```
sudo dpkg --configure -a
```

enter password

Edit ```
sudo apt-get update
```

---

### Post by elquer on 2007-07-22
thank you, worked out

---

