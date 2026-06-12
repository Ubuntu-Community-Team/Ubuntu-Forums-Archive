---
title: "Enemy Territory install?"
date: 2005-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by psoulocybe on 2005-04-24
I want to install enemy territory, any tips on what to do to get it to work...
here is my error message:

This installation doesn't support glibc-2.1 on Linux / x86_64
(tried to run setup)
See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
The setup program seems to have failed on x86_64/glibc-2.1

---

### Post by psoulocybe on 2005-04-24
Ok, so i found how to install the ia32 libs and linux32.

linux32 sh et-linux-2.55.x86.run

and i get this


/tmp/selfgz18060/setup.sh: line 143: 18153 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.0


I'm stumped now...   the directions I got were from here: [http://ubuntuforums.org/archive/index.php/t-20268.html](http://ubuntuforums.org/archive/index.php/t-20268.html)

---

### Post by psoulocybe on 2005-04-25
Anybody have a clue on this one?

---

### Post by psoulocybe on 2005-04-28
Ok... installed fine.

now.....  when i try to

linux32 et

i get:

loading libGL.so.1: Received signal 11, exiting...

---

### Post by flex447 on 2005-05-07
I get that ...loading libGL.so.1: Received signal 11, exiting...

---

### Post by flex447 on 2005-05-10
You could try this..

[http://ubuntuforums.org/archive/index.php/t-20268.html](http://ubuntuforums.org/archive/index.php/t-20268.html)

---

