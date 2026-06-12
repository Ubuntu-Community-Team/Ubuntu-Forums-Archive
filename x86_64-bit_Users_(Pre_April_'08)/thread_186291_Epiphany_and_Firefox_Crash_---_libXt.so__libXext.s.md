---
title: "Epiphany and Firefox Crash --- libXt.so / libXext.so Error"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sykil on 2006-06-01
```
stephen@astarael:~$ epiphany

(epiphany:5884): libgnomevfs-WARNING **: Failed to create service browser: Bad state

LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
stephen@astarael:~$

```
Happens with both Firefox and Epiphany. Any ideas?

---

### Post by Sykil on 2006-06-01
Nevermind, fixed. Sorry about that.

**For those of you in the future who have this problem: try installing libxt-dev**

---

