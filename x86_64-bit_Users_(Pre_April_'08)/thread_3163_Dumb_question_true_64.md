---
title: "Dumb question: true 64??"
date: 2004-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by jdusablon on 2004-11-03
How much of ubuntu64 is true 64-bit?? I imagine the kernel and the most common interfaces and apps, but:

- Are there completely separate repositories and 64-bit packages?
- Do some parts of the OS run in 32-bit virtual spaces?
- Can one run a 32-bit apps/processes in a 32bit virtual space?
- Is there or will there ever be a SPARC64 Ubuntu and/or G5/Power5 Ubuntu?

Sorry I don't have AMD64, so I don't know these things. But I'm slowly researching this stuff so I know whether to Opteron or G5 when the time comes.

---

### Post by jdodson on 2004-11-04
to my knowledge ubuntu maintains different AMD64 packages than the other arch. types.  it would seem that if they do maintain different packages that the different packages are compiled for 64 bit.  i am not sure ALL packages that are in the main x386 universe are in the AMD64 universe however.   if the packages are compiled for AMD64 then they would be 'true' 64 bit applications able to handle 64 bit registers, etc.  however i make a few assumptions that could be better answered by a developer.

and to my knowledge ubuntu handles 3 different proc types x386, AMD64 and PPC, not sure if they will add anymore in the future.

---

### Post by Werpon on 2004-11-07
All executables I've checked are compiled for AMD64:

```
$ file /bin/bash
/bin/bash: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.4.0, dynamically linked (uses shared libs), stripped
```

I know Fedora for AMD64 can run i386 progs, so Ubuntu should, too. I don't know how to install them, though...

---

### Post by HiddenWolf on 2004-11-13
Ofcourse compiled for 64 bit is something else entirely than written for 64 bit, which would gain us much more speed/efficiency-wise.

---

