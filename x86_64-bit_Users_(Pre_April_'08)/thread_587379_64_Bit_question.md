---
title: "64 Bit question"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by deamon_knight on 2007-10-22
I want to make the move to linux,  and any new box would have a 64bit CPU. I want to, *eventually*, learn to compile my own Live CD for diagnostic purposes. However, I'd probably need to make that a 32bit version for compatibility. If I install a 64bit version, can I then compile and make a 32bit liveCD sometime down the road?

---

### Post by John.Michael.Kane on 2007-10-22
> **deamon_knight said:**
> I want to make the move to linux,  and any new box would have a 64bit CPU. I want to, *eventually*, learn to compile my own Live CD for diagnostic purposes. However, I'd probably need to make that a 32bit version for compatibility. If I install a 64bit version, can I then compile and make a 32bit liveCD sometime down the road?

You can compile programs to be 32bit under 64bit.

Depending on how you plan to do it you would use the -m32 and -m64 option. These options generate code for 32-bit or 64-bit environments.

The 32-bit environment should set int, long and pointer to 32 bits and generate code that runs on any i386 system.

The 64-bit environment should set int to 32 bits and long and pointer to 64 bits and generate code for AMD&#8217;s x86-64 architecture.

You can pass -m64 or -m32 like so.
For 32 bit version:
```
gcc -m32 -o output32 foo.c
```
For 64 bit version :
```
gcc -m64 -o output64 foo.c
```

The other method would be to set up a 32-bit chroot environment 
[Setting up 32-bit chroot environment ]("http://jrblevin.freeshell.org/linux/chroot/")

Hope this helps.

---

