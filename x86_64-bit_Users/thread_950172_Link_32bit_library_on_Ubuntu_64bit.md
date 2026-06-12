---
title: "Link 32bit library on Ubuntu 64bit"
date: 2008-10-16
forum: x86 64-bit Users
---

### Post by sensius on 2008-10-16
Hi guys,

My Ubuntu is a 64bit version. When I compile a project using Codeblocks, there are some errors/warnings at linking step; says the warning: "/usr/bin/ld: i386 architecture of input file `/usr/lib/libNewton.a(dgConvexCollision.o)' is incompatible with i386:x86-64 output"

So, how do I link/generate 32bit libraries on 64 bit OS?

Many thanks

---

### Post by Kilz on 2008-10-16
[Getlibs ]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs")should help you install the files.

---

### Post by Yellow Pasque on 2008-10-16
I'm not sure about CodeBlocks, but when you compile with gcc for a 32-bit target, use the -m32 flag.
Make sure you have your multilib packages installed:
```
sudo apt-get install gcc-multilib g++-multilib
```

---

### Post by sensius on 2008-10-17
thanks all guys. That's would be a great help :KS

---

### Post by sensius on 2008-10-17
Just one more question.

Can I mix (link) some 32bit libraries with others of 64bit version?

---

### Post by Kilz on 2008-10-17
> **sensius said:**
> Just one more question.

Can I mix (link) some 32bit libraries with others of 64bit version?

You dont mix libraries. In a 64bit install there is /usr/lib for 64bit libraries and /usr/lib32 for 32bit libraries. So what you end up with libraries for both 64 and 32 sometimes. Thats why I recommended getlibs, it places things where they need to go. Never, ever force install libraries.

---

