---
title: "compiling for 32 bit"
date: 2006-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by jtgd on 2006-12-30
I am running Edgy on Opterons.  I need to compile a static binary for 32bit to run on a different machine.  On Gentoo I was able to install a 32bit g++ compiler, but I don't see that in adept.  When I compile

**g++ -m32 -static -march=i386 **

I get

[B]/usr/bin/ld: skipping incompatible /usr/bin/../lib/libm.a when searching for -lm
/usr/bin/ld: skipping incompatible /usr/lib/libm.a when searching for -lm
/usr/bin/ld: cannot find -lm
[/B]

so it seems to be a missing library problem.  I'm not sure if I really need to install the whole compiler or not.  Could I just supply some libraries?  And if so, where do I get them?

Any advice?  Thanks.

---

