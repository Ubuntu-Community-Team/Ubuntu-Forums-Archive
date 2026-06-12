---
title: "mplayer/mencoder problems"
date: 2005-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by bannerboy on 2005-12-20
I instlled the mencoder-amd64 and mplayer-amd64 packages and mplayer doesn't work at all, and mencoder segfaults, what do I do?

---

### Post by kairu0 on 2005-12-20
What are the symptoms for mplayer?

---

### Post by bannerboy on 2005-12-20
mplayer-amd64 crashes whenever I try to play a dvd:

```
MPlayer interrupted by signal 11 in module: decode_audio
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed
```

---

