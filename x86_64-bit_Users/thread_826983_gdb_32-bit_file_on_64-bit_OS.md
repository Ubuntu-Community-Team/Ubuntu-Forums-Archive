---
title: "gdb 32-bit file on 64-bit OS"
date: 2008-06-12
forum: x86 64-bit Users
---

### Post by strattonbrazil on 2008-06-12
I'm trying to run gdb on a program built for 32-bit but my machine is 64-bit and is complaining about being built for only 64-bit machines.  Is there a way to run gdb on 32-bit programs even though it was compiled for 64-bit?  

Linux iceman 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux

```

gdb ./bin/visit
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
"/home/josh/visit/stratton/amr2/src/bin/visit": not in executable format: File format not recognized

```

---

### Post by Jouke74 on 2008-06-12
I don't think so. 

It's better to compile it for 32 bit on the 32 bit machine itself, install it through the package manager of that machine, or use a repository or 3rd party source for the 32 bit executable.

EDIT : Ehhh interpreted it wrong as running a 64 bit program in 32 bit environment.

---

### Post by Sef on 2008-06-12
> Is there a way to run gdb on 32-bit programs even though it was compiled for 64-bit? 

Yes, there is.  Check [this post]("http://ubuntuforums.org/showthread.php?t=474790").

---

