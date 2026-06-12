---
title: "[SOLVED] alienarena2008"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by soxs on 2008-05-20
What is required to build alienarena (on 64 bit hardy heron)? (No, I am not going to download/use the deb packages)

```
apt-get build-dep alien-arena
``` does not work :-/

---

### Post by soxs on 2008-05-20
Omg-.- I am so stupid, it only has 32bit executables.

I finally got it running (compiling got a useless option) via ```
getlibs ./crx
``` from the folder where crx is located.

See: [http://gaming.gwos.org/doku.php/guides:64bit:alien_arena](http://gaming.gwos.org/doku.php/guides:64bit:alien_arena)
And: [http://ubuntuforums.org/showthread.php?t=717132&page=1](http://ubuntuforums.org/showthread.php?t=717132&page=1)

---

