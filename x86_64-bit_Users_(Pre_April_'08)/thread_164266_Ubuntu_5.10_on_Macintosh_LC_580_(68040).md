---
title: "Ubuntu 5.10 on Macintosh LC 580 (68040)"
date: 2006-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by n7tzg on 2006-04-22
I know that the power pc group is supported, but is it possible to install on a 68040 Mac?

---

### Post by ssam on 2006-04-22
ubuntu does not have a 68k port, but i think debian does, see [http://www.us.debian.org/ports/m68k/](http://www.us.debian.org/ports/m68k/) . or try netbsd [http://www.netbsd.org/Ports/mac68k/](http://www.netbsd.org/Ports/mac68k/)

---

### Post by jdp on 2006-04-22
the LC 580 has a 68LC040, which means taht there is no FPU.  You'd need to either use the NetBSD branch with SoftFloat compiled in, or swap in a full 68040 CPU.

Back in the day I used to run NetBSD on my LC 580CD with a full 68040, but I haven't played with it much since somebody built up the FPU-less versions.

---

### Post by Doobie9 on 2006-04-22
[QUOTE=n7tzg]I know that the power pc group is supported, but is it possible to install on a 68040 Mac?[/QUOTE]

There's only one Linux I know of that can be installed on a 68k: [http://www.mac.linux-m68k.org/](http://www.mac.linux-m68k.org/)

There may be others, so look around. I once tried to install it and it's very hard, and I had no success.

---

