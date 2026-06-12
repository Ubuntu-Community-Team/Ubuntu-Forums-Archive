---
title: "[SOLVED] libqt3-mt, needed and breaking updates!"
date: 2007-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by tarekeldeeb on 2007-11-13
Hello all Ubuntains :popcorn:

I have an AMD64/Gutsy .. running opera32, skype ..

both neeed the libqt3-mt to run .. everything went ok ..

Then i installed a bunch of programs .. and they work
but opera stopped opening .. and complemented that libqt3-mt cannot be loaded ..

I re-installed the needed library .. opera is fine again ..

Then I noticed the update icon beside the clock .. but the update manager refused complaining that the SW index is refused , and I have to run "sudo apt-get install -f"

and I did , this is the result:
> Correcting dependencies... Done
The following extra packages will be installed:
  libqt3-mt
Suggested packages:
  libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc
The following NEW packages will be installed:
  libqt3-mt
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3645kB of archives.
After unpacking 11.6MB of additional disk space will be used.
Do you want to continue [Y/n]?

if i chose yes .. this breaks the libqt3-mt, and i need to install it again,
if no .. the apt-get is still broken, but opera is alive!

when i started the synaptic, i knew that asvn had the broken dependency ..
do i have to remove it ?
or there is another solution to run both opera32 and asvn?

---

### Post by Cappy on 2007-11-13
Do the ```
sudo apt-get install -f
``` and let it install the libqt3-mt 64-bit library on your machine.

Install getlibs here:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

and then run
```
sudo getlibs -32 libqt-mt.so.3
```

This problem arises when you force-install a 32-bit library - it will overwrite any 64-bit library with the same name which can causes this dependency problem.

---

### Post by tarekeldeeb on 2007-11-14
thanks .. :)

---

