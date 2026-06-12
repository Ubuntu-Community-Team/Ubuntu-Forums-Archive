---
title: "problem with acroread using dchroot"
date: 2007-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrdean on 2007-01-21
I try to run Acrobat Reader using dchroot.

In 64 bit mode :
$ acroread32 
I: [edgy chroot] Running command: “acroread32 ”
/bin/bash: acroread32: command not found

$ ls -l /usr/local/bin/acroread32 
lrwxrwxrwx 1 root root 25 2007-01-21 23:56 /usr/local/bin/acroread32 -> /usr/local/bin/do_dchroot

But, if I do $ dchkroot -d
and afterwards
$ acroread
it works.

What I'm doing wrong?

Thanks.

---

### Post by kuja on 2007-01-21
Well, sounds like you're doing things the hard way (in my opinion). Anyway, one thing to check is that /usr/local/bin is in your $PATH. Also check that /usr/local/bin/do_dchroot is marked executable.

---

