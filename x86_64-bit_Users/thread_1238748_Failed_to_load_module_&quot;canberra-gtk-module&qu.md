---
title: "Failed to load module &quot;canberra-gtk-module&quot;"
date: 2009-08-12
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2009-08-12
Hi guys,

Another question.  I just migrated from Ubuntu to KUbuntu.

When I use gedit or kate or ... to open a file I am receive the following errors.
 
marc@marc-desktop:~$ gksudo kate /etc/sources.list
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: unable to open shared objectfile: No such file or folder.

marc@marc-desktop:~$ gksudo kate /etc/modprobe.d/sound
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: unable to open shared objectfile: No such file or folder.

* when I end the kate sesstion (Alt F4) the following is printed:
QThreadStorage: Thread 0x1738470 exited after QThreadStorage 2147483637 destroyed
marc@marc-desktop:~$

Maybe you can help me, I am puzzeld


Cheerz

---

### Post by Yellow Pasque on 2009-08-12
Use kdesu or kdesudo instead of gksudo. Or install the corresponding libcanberra-gtk-module package.

---

### Post by Bloemetjesgordijn on 2009-08-13
thx it worked

---

