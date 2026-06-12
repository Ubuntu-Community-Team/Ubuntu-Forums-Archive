---
title: "Installing Unreal tournament GOTY 99"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by Majin Zero on 2009-11-05
Ok, I enter:

./unreal.tournament_436-multilanguage.goty.run


and this is what outputs:

error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


I followed a guide and manually copied some files from an extracted i386 deb package to my lib32 folder, and that didn't solve the issue.

I tried copying the files to my /lib folder, and I got a different error output:

error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS32

any ideas?

---

