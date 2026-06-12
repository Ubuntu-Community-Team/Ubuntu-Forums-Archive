---
title: "Dual Boot"
date: 2008-06-03
forum: x86 64-bit Users
---

### Post by miket3115 on 2008-06-03
Hi I've been running a dual boot machine with Ubuntu and windows XP. I started out with Ubuntu 7.1 and up graded to 8.04 when it was released.  The problem I'm having is this, when I first installed Ubuntu, the boot loaded at startup showed very few options re-guarding the choice of operation systems.  ie

Ubuntu generic 7.10
Ubuntu 7.10 safe mode 
Windows XP home.

Now however, when I start up I'm getting what looks to be like duplicate or redundant options like this

Ubuntu 8.04
Ubuntu 8.04 safe mode
Ubuntu 8.04
Ubuntu 8.04 safe mode
Ubuntu 8.04
Ubuntu 8.04 safe mode
Windows XP home.

Is there any reason for this? Can It be fixed and if so how would I go about reverting it back to a simpler Boot menu?

Thanks 

Mike

---

### Post by Sef on 2008-06-03
It's different kernels.  Gutys had one set of kernels and Hardy has an updated set of kernels.  With each kernel there is a regular mode and a safe mode.

---

### Post by miket3115 on 2008-06-04
OK that clears up that thanks for the help, now is there a way to delete the old kernels?

---

### Post by razvi on 2008-06-06
Yes.Edit boot/grub/menu.lst file and keep whatever you want to be shown at boot time. You must have admin privileges to edit this file.

---

### Post by miket3115 on 2008-06-06
Ok thanks I'll give it a try and see what happens

---

### Post by Yellow Pasque on 2008-06-06
Make sure to backup your menu.lst file! You don't want to hose that one :P
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```

---

