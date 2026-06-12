---
title: "libmikmod.so.2: cannot open shared object file"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by Bulletbeast on 2008-11-13
When trying to start OHRRPGCE (an app which depends on SDL_mixer, which seems to depend on said libmikmod), I get this:

ohrrpgce-game: error while loading shared libraries: libmikmod.so.2: cannot open shared object file: No such file or directory

ohrrpgce-custom: error while loading shared libraries: libmikmod.so.2: cannot open shared object file: No such file or directory

ldd ohrrpgce-game or ohrrpgce-custom yields:

...
	libmikmod.so.2 => not found
	libvorbisfile.so.3 => not found
	libsmpeg-0.4.so.0 => not found
...

In fact, at least the first one is in /usr/lib. I tried copying the symlink to /usr/lib32, which results in:

ohrrpgce-game: error while loading shared libraries: libmikmod.so.2: wrong ELF class: ELFCLASS64

---

### Post by Cappy on 2008-11-13
Install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run
```
getlibs -l libmikmod.so.2 libvorbisfile.so.3 libsmpeg-0.4.so.0
```

---

### Post by Bulletbeast on 2008-11-14
Worked, and this tool's just what I need. Thanks a lot (:

---

### Post by Yellow Pasque on 2008-11-14
> I tried copying the symlink to /usr/lib32
Don't do that again. Only put 32-bit libs in /usr/lib32.

---

