---
title: "How to cross compile"
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by rpm11 on 2006-08-02
Hi all,

I am desperatly trying to compile 32 bit binaries on a amd64 dapper machine. I've installed all ia32* packages. gcc 4.0 seems to have multilib activated but gcc -m32 still end up in libraries not found..
In breezy a package ia32-libs-dev existed but it seems to be gone in dapper.

UPDATE: What I wrote above is not true: Compiling c-code works, but I just saw that g++ (v4.0, v3.3) is configured with --disable-multilib.
Why that??

Thanks a lot for any help or explanation !!

---

