---
title: "Firefox 1.5 on 64-bit"
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by thread on 2005-11-29
Woot! Firefox 1.5 came out today. Now, where are the 64 bit (x86_64 if you searched for that) debs at? I would be content to compile it, but it bombs out... what does it mean and how does one fix it?

```

thread@thread:~/src/mozilla$ ./configure --prefix=/home/thread/apps/firefox --enable-application=browser --enable-application=mail && make
... snip ...
c++  -fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -pedantic -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -O -fPIC -shared -Wl,-h -Wl,libmozz.so -o libmozz.so  adler32.o compress.o crc32.o deflate.o gzio.o infback.o inffast.o inflate.o inftrees.o trees.o uncompr.o zutil.o        -ldl -lm
/usr/bin/ld: deflate.o: relocation R_X86_64_PC32 against `memcpy@@GLIBC_2.2.5' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: final link failed: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libmozz.so] Error 1
make[3]: Leaving directory `/home/thread/src/mozilla/modules/zlib/src'
make[2]: *** [libs] Error 2
make[2]: Leaving directory `/home/thread/src/mozilla/modules/zlib'
make[1]: *** [tier_1] Error 2
make[1]: Leaving directory `/home/thread/src/mozilla'
make: *** [default] Error 2

```

---

### Post by Benjamin_Lebsanft on 2005-11-30
would be nice, yes!

---

### Post by RAOF on 2005-11-30
If you don't mind running the 32bit version, there's always my howto.[http://www.ubuntuforums.org/showthread.php?t=90106]("http://www.ubuntuforums.org/showthread.php?t=90106")

---

### Post by Casey on 2005-11-30
from your post: 
```
recompile with -fPIC
```

Perhaps trying that will help?

---

### Post by shadesfox on 2005-11-30
It does get compiled -fPIC.  This is a bug in the Ubuntu tool chain.  I forget which part's fault it is, I want to say it is a bug in binutils.

The fix is to add this option to your .mozconfig
```
ac_cv_visibility_pragma=no
```
I would reccomend removing the whole mozilla source directory and restarting with a fresh source tree before adding that option.

I'm still trying to fine tune the build options, I'm still getting some screwy behavior from firefox.  Book marks don't load properly and after customizing the toolbars they toolbars start acting strange.  Though I think that is my fault for my build options.  Though I must say I'm impressed with the results of changing "-O2" to "-Os"  Seems to make firefox a lot more snappy.

Oh yes, don't build with Pango enabled either.

---

### Post by thread on 2005-11-30
Thank you ShadesFox! I don't know if it was .mozconfig in the firefox src root or ~/.mozconfig, but I created both and it appears to be compiling now...

Where does one add this -Os flag? I know -O2 is the standard optimization level and while -O3 usually works fine, going higher is at one's own risk.... what is -Os? I haven't encountered this.

---

### Post by RAOF on 2005-11-30
-Os is optimize for **s**ize, rather than speed.  It can, however, improve speed because a smaller executable means it is more likely to fit in whatever cache the processor has, and memory access is the limiting factor for many programs (this is in fact the reason for Intel's hyperthreading - by having more possible code to run, the CPU can mitigate the huge (like thousands of clock-cycles) wait for memory, should an instruction request data not in the caches).

---

### Post by bugmenot on 2005-12-25
See gcc bug:
[http://gcc.gnu.org/bugzilla/show_bug.cgi?id=20297](http://gcc.gnu.org/bugzilla/show_bug.cgi?id=20297)
Also Red Hat bug:
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=150157](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=150157)

---

### Post by Ellric on 2006-01-13
WOOT! it worked! Firefox 1.5 on my AMD64 Ubuntu! Finaly! 

Thanks! :razz:

---

### Post by mattbarlow on 2006-01-14
any .deb for firefox 1.5 for amd 64??
Or am i asking for too much?

---

