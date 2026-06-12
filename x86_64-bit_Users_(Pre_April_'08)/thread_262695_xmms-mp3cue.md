---
title: "xmms-mp3cue"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by code-breaker on 2006-09-22
Can someone explain (preferrably in painful detail) how to get xmms-mp3cue installed on an amd64 (dapper) machine?

```

$ make
g++ -o libmp3cue.so mp3cue.o cuesheet.o interface.o ID3tag.o -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lxmms -shared
/usr/bin/ld: mp3cue.o: relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
mp3cue.o: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [mp3cue] Error 1

```

---

