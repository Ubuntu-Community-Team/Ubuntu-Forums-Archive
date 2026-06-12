---
title: "Skype 1.4 Beta does not like my KDE 4"
date: 2007-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aleksandersen on 2007-06-16
Hi,

I installed the [Skype 1.4 Beta](http://www.skype.com/intl/en/download/skype/linux/) on my KUbuntu 7.04 (64 bits) with **sudo dpkg -i --force-architecture skype*.deb**. However the new beta does not like me. At least it complains:

> $ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory

How to fix?

---

### Post by gbesso on 2007-06-16
Since you had to use --force-architecture I'm guessing it's a 32bit program, so you need the required 32-bit libraries installed in /usr/lib32.

You should try [this script]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") by Cappy.
Otherwise, you need to get the libqt4-core-kdecopy package from [http://packages.ubuntulinux.org]("http://packages.ubuntulinux.org")
use dpkg -x to extract it, copy the contents of usr/lib inside the package to /usr/lib32, and repeat with more libraries until you finish. 

The script mentioned above should do it much more easily.
Good luck!

---

### Post by Aleksandersen on 2007-06-16
Thanks. The script did the trick.

(PS: The new Skype looks really nice! :)

---

### Post by Cappy on 2007-06-16
Aleksandersen,
I also have a script that will solve binary dependencies automatically ;)
See my new script:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

