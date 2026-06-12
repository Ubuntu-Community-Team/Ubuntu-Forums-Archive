---
title: "fPIC problem while installing ruby gems"
date: 2008-09-01
forum: x86 64-bit Users
---

### Post by Casla on 2008-09-01
Thanks for getting to my post, I have been having this problem for couple of days now. when I try to install rmagick with 'gem install' I get this error:

/usr/bin/ld: /usr/local/lib/libz.a(inflate.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libz.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make: *** [RMagick2.so] Error 1

I have had similar fPIC error when i try to install ImageMagick from source. I couldn't resolve it by adding -fPIC flags so I skipped the problem by installing it through apt-get.

But now when I try to install the rmagick gem, the same error pops up on the same file '/usr/local/lib/libz.a' only this time i think its trying to compile to a different object (inflate.o).

Could someone please help me with this?

I am suspecting that this is got something to do with been on AMD64 ubuntu, hence I posted here hope its ok.

Many thanks

---

### Post by Casla on 2008-09-01
Ok, I managed to fix this. Just for in case someone else have the same problem.

This is caused by gcc using the libz.a file in /usr/local/lib instead of the one in /usr/lib64 to compile RMagick2.so.

I added /usr/lib64 to the LIBPATH in the Makefile, and this seems to fixed it.

---

