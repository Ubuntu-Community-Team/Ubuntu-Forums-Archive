---
title: "python-psyco package not available"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by narcisgarcia on 2008-05-20
In Ubuntu GNU/Linux 8.04 (Hardy Heron) -AMD64, the repositories only include the "python-psyco-doc" package, but not the binary "python-psyco".

This can bee seen on:
[http://packages.ubuntu.com/hardy/python-psyco-doc](http://packages.ubuntu.com/hardy/python-psyco-doc)
and:
[http://packages.ubuntu.com/hardy/python-psyco](http://packages.ubuntu.com/hardy/python-psyco)

---

### Post by Saghaulor on 2008-08-11
> **narcisgarcia said:**
> In Ubuntu GNU/Linux 8.04 (Hardy Heron) -AMD64, the repositories only include the "python-psyco-doc" package, but not the binary "python-psyco".

This can bee seen on:
[http://packages.ubuntu.com/hardy/python-psyco-doc](http://packages.ubuntu.com/hardy/python-psyco-doc)
and:
[http://packages.ubuntu.com/hardy/python-psyco](http://packages.ubuntu.com/hardy/python-psyco)

Psyco will not be supported for x86 64 processors. 

[http://psyco.sourceforge.net/introduction.html](http://psyco.sourceforge.net/introduction.html)

> Drawbacks

    Psyco currently uses a lot of memory. It only runs on Intel 386-compatible processors (under any OS) right now. There are some subtle semantic differences (i.e. bugs) with the way Python works; they should not be apparent in most programs.


[http://psyco.sourceforge.net/psycoguide/req.html](http://psyco.sourceforge.net/psycoguide/req.html)

> 1.1 Requirements

Psyco requires:

    * A 32-bit architecture. A Pentium or any other Intel 386 compatible processor is recommended.

    * Linux, Mac OS/X, Windows, BSD are known to work.

    * A regular Python installation, version 2.2.2 or up. Psyco is not a replacement for the Python interpreter and libraries, it works on top of them.

Psyco is not strongly dependent on a particular OS. Precompiled binaries for Windows are contributed by users. Compiling on Linux, Mac OS/X and other Unixes should be easy.

Psyco has an emulation mode that allows it to run on other 32-bit processors but the speed benefits are not big in that case. Psyco does not support the 64-bit x86 architecture, unless you have a Python compiled in 32-bit compatibility mode. There are no plans to port Psyco to 64-bit architectures. This would be rather involved. Psyco is only being maintained, not further developed. The development efforts of the author are now focused on PyPy, which includes Psyco-like techniques. [http://codespeak.net/pypy/](http://codespeak.net/pypy/) 

My question, however, is there a way to get it running on x86 64 processors, and will it have any performance gains if it can be run on said architecture?

---

### Post by letshavepaneer on 2008-08-11
I have the same issue.  I run a small program that does some computation, in Windows, I run this and it runs really quickly.  In ubuntu, it runs much more slowly.

I'm torn because I'm using the 64-bit version, so you'd think there would be a big benefit to that performance-wise, although this is not the case of a critical optimization package does not work.

I'd like to try to use PyPy, and see if this would work as a replacement, but PyPy seems to have no modules associated with it, particularly, I'd like to use the python package called "matplotlib"....

---

### Post by irishbeer on 2009-08-24
same here... using Jaunty and AMD 64

---

### Post by frikker on 2009-09-21
I just installed Ubuntu on my Macbook (2,1 - core 2 duo).  When I was using OS X, psyco worked just fine for me.  I remember psyco did not work a few years ago on my macbook, but sometime this year 1.6 came out with support for OSX/Intel and it has worked great since.

I am pretty sure OS X 10.5, which is what I was running, runs in 64-bit mode.  So why no linux support?  Is it a matter of running python in 32-bit mode, perhaps as OS X is doing?

Blaine

---

