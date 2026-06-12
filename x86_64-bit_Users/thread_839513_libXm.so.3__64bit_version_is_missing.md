---
title: "libXm.so.3  64bit version is missing"
date: 2008-06-24
forum: x86 64-bit Users
---

### Post by yiorgos on 2008-06-24
I've just installed a commercial product on a 64bit Feisty,
and I am facing a weird problem with libXm.so.3.

If I try to start the program I get an error message that the libXm.so.3,
is missing. After some trial and error I found that it seeks in the /usr/lib32 directory.
So I made a symbolic link to the /usr/lib/libXm.so.3.

But then I got the error message
[I]error while loading shared libraries: libXm.so.3: wrong ELF class: ELFCLASS64
[/I]indicating that it needs the 64 bit version of the library to run.
But the weirdness is that it seeks to the lib**32** directory for a 64bit library!
Anyway, apart from the above weirdness I can't find any 64bit Debian version for the libray, there's only rpm packages for redhat distros.

Any suggestions?
Thnx in advance

---

### Post by kuja on 2008-06-24
No, that error indicates that it needs the ***32*** bit library to run.

Two easy ways to grab it, look into getlibs, or download the package (libmotif3), extract it with dpkg -x, and copy the files from the extracted/usr/lib/ to /usr/lib32.

---

### Post by yiorgos on 2008-06-25
> **kuja said:**
> No, that error indicates that it needs the ***32*** bit library to run.

Two easy ways to grab it, look into getlibs, or download the package (libmotif3), extract it with dpkg -x, and copy the files from the extracted/usr/lib/ to /usr/lib32.

Thanks!
worked like a charm!

---

