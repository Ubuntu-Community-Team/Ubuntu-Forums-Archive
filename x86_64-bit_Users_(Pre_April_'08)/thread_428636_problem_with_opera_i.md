---
title: "problem with opera i"
date: 2007-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by quade888 on 2007-04-30
i was clumsy when trying to get sound in flash in opera and by accident managed to delete the  /usr/lib32/ folder

when trying to start opera now i get this error

thomas@thomas-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.20-20070409.1/opera: error while loading shared libraries: libX11.so.6: wrong ELF class: ELFCLASS64
thomas@thomas-desktop:~$ 

i assume this outcome is somehow affiliated with my clumsiness. Do anyone have a clue as to how i can solve this/restore the /usr/lib32 folder with the appropriate files in it?

---

### Post by kuja on 2007-04-30
I would try reinstalling all of the ia32-libs packages, that should be a good start. Oh, and for sound in opera all you should need is lib32asound2

---

