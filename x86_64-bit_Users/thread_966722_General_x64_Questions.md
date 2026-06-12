---
title: "General x64 Questions"
date: 2008-11-01
forum: x86 64-bit Users
---

### Post by Ramzy on 2008-11-01
Howdy,

How does the x64 version of Ubuntu 8.10 handle emulation of 32 bit software?

For instance, Windows XP x64 was an abysmal failure... However Vista x64 has nearly no problems whatsoever, and the experience runs as flawlessly as the 32 bit version, as well as being able to seperate 32 bit software completely.

[img]http://i36.tinypic.com/28lyi6t.png[/img]

I'm not very fond of using a 32 bit OS as that would make my 8GB of RAM completely useless, so i would like to know just how well Ubuntu x64 runs and if i'll be encountering too many issues to make using it worth the trouble.

Thanks.

---

### Post by dfreer on 2008-11-01
x86_64 processors running a 64-bit OS can execute 32-bit binaries. The main thing is that if the 32-bit binary needs to use some shared libraries, those libraries must also be 32-bit.

For the most part, common 32-bit libraries are installed in Ubuntu under the package name ia32-libs. These libraries should enable most 32-bit binaries to run, but in case the binary needs more, you can always install the other 32-bit binaries.

---

### Post by stmiller on 2008-11-01
As dfreer states, Ubuntu and Debian 64bit both can execute 32bit apps as normal. It is very mature vs. the current state of 32bit-under-64bit in Windows.

64bit Linux with those ia32 packages installed has:

/usr/lib64/ (...sym link to /usr/lib/)

and

/usr/lib32/


You can also do:
```

$ linux32 program

```
if needed. :KS

---

### Post by noerrorsfound on 2008-11-01
> **Ramzy said:**
> For instance, Windows XP x64 was an abysmal failure... However Vista x64 has nearly no problems whatsoever, and the experience runs as flawlessly as the 32 bit version, as well as being able to seperate 32 bit software completely.
XP x64 was a failure? Oh, really? I haven't had any problems with it, and it has run every 32-bit application **flawlessly**.

It also does the exact same thing you mentioned about separating 32-bit and 64-bit programs. That's why XP x64 has two folders: Program Files and Program Files (x86).

---

### Post by jespdj on 2008-11-01
You can't compare 64-bit Windows directly with 64-bit Ubuntu. I've never used 64-bit Windows, but as far as I know most of the problems there are because many device manufacturers don't bother to write 64-bit drivers and there isn't that much 64-bit native Windows software.

On Linux, you don't have that problem because almost all software is open source, so almost all drivers and applications have been compiled as 64-bit native executables.

I've been using 64-bit Ubuntu for a year now, and it works just as well as the 32-bit version. I have only two 32-bit programs on my computer, and they're both closed source proprietary programs: Skype and Adobe Flash.

So, if 64-bit Windows doesn't work well for you, don't assume that any other 64-bit OS will be just as bad.

---

### Post by dfreer on 2008-11-01
> **noerrorsfound said:**
> XP x64 was a failure? Oh, really? I haven't had any problems with it, and it has run every 32-bit application **flawlessly**.

It also does the exact same thing you mentioned about separating 32-bit and 64-bit programs. That's why XP x64 has two folders: Program Files and Program Files (x86).

Ubuntu/debian only separates the libs, badly at that actually. It is currently not true multi-arch, which is important for users to understand I think.

Right now, on a 32-bit install 32-bit libs are placed in /usr/lib/. On a 64-bit install, 64-bit libs are ALSO placed in /usr/lib/. A true multi-arch would place them in /usr/lib64/ and /usr/lib32/ regardless of the arch the OS is running (even further multi-arch would include ppc 32/64 bit libs, like /usr/linux/lib32 and /usr/ppc/lib32 but whatever).

Furthermore, programs installed with a debian package manager are not installed based on what arch they are intended to run on. So for example firefox, it's 64-bit package places a 64-bit binary at /usr/bin/firefox. The 32-bit package places it's 32-bit binary also at /usr/bin/firefox, which means that it would be impossible to install both a 32-bit and a 64-bit at the same time unless you did it manually.

There's nothing *wrong* with running 64-bit, and I enjoy running it with absolutely no problems that are caused by running a 64-bit OS, just problems that would affect me regardless of which arch I choose.

If Debian/Ubuntu was truly mult-arch, you could install the 64-bit OS, open up your favorite package manager, and when you find the software you want to install you will be able to select whether you want to install the 32-bit, the 64-bit, or both packages together. You would use the same repositories as the 32-bit users and have access to programs that are only availble as 32-bit packages.

[http://lackof.org/taggart/hacking/multiarch/](http://lackof.org/taggart/hacking/multiarch/)

---

### Post by xen-uno on 2008-11-01
"For instance, Windows XP x64 was an abysmal failure"

At what? ... explain that. To me, XP x64 is what Vista should have been. I've got a mix of 32 & 64 bit apps a mile long and haven't had any trouble what-so-ever.

---

