---
title: "wrong kernel for amd64?"
date: 2009-06-08
forum: x86 64-bit Users
---

### Post by mackra on 2009-06-08
Hey,

I've had 9.04 installed on a new system for a couple months already and it's (generally) working fine.

But 
$ uname -a

produces

Linux ubuntuamd64 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

Shouldn't it be something like 2.6.28-11-amd64? I did install from a 64bit disk.  If this is the incorrect kernel, how do I install the correct one without doing a complete install?

Rich

---

### Post by John.Michael.Kane on 2009-06-08
> **mackra said:**
> Hey,

I've had 9.04 installed on a new system for a couple months already and it's (generally) working fine.

But 
$ uname -a

produces

Linux ubuntuamd64 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

Shouldn't it be something like 2.6.28-11-amd64? I did install from a 64bit disk.  If this is the incorrect kernel, how do I install the correct one without doing a complete install?

Rich

That is the correct kernel. The part that states x86_64 means your kernel is 64 bit.

Example from my test machine.
```
desktop 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:31:32 UTC 2009 **x86_64** GNU/Linux
```

---

### Post by mackra on 2009-06-08
Why does my Debian Squeeze show amd64?

Rich

---

### Post by ptn107 on 2009-06-08
Different distributions name their kernels in different ways.  My Debian squeeze shows x86_64 with 'uname -a'.

---

### Post by mackra on 2009-06-08
This is from my laptop which I've upgraded to Squeeze over the weekend.

$ uname -a
Linux delldebian 2.6.26-2-amd64 #1 SMP Thu May 28 21:28:49 UTC 2009 x86_64 GNU/Linux

Rich

---

### Post by jespdj on 2009-06-09
Ubuntu is derived from Debian, but it is not exactly the same as Debian. It's normal for Ubuntu that the kernel name ends with "...-generic" and not "...-amd64" as with Debian.

As said above, "x86_64" means that you're using the 64-bit version of Ubuntu.

So, there's nothing wrong and nothing to worry about here.

---

### Post by mackra on 2009-06-09
Good!  Thanks to both of you.  I can sleep tonight, ha ha.

Rich

---

