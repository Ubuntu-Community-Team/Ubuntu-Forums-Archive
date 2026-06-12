---
title: "projectM 0.99 compile fail on Dapper/AMD64"
date: 2006-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by ktulu1115 on 2006-07-21
I tried downloading and compiling the latest projectM for use with XMMS and got the following error during the 'make': 
 
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC 
/usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../../lib64/libftgl.a: could not read symbols: Bad value 
collect2: ld returned 1 exit status 
make[2]: *** [libprojectM.la] Error 1 
make[2]: Leaving directory `/home/ktulu/usr/libprojectM/src' 
make[1]: *** [all-recursive] Error 1 
make[1]: Leaving directory `/home/ktulu/usr/libprojectM' 
make: *** [all] Error 2 
 
I'd guess that it's an issue with FTGL on 64-bit systems - anyone else ever experience this?

---

### Post by RAOF on 2006-07-21
Not your specific problem, but I **have** had a similar one.  You get the same error when trying to build ffmpeg & link in DTS.  It turns out that Ubuntu builds two libraries: libdts.a **without** PIC, and libdts_pic.a **with** PIC.  Simply changing the linking of -ldts to -ldts_pic in the ffmpeg configure scripts makes it build.

Not **exactly** the same problem as you have, but about as close as you'll get without finding that package in my repository :).  I'd look for a libftgl_pic.a, possibly?

---

### Post by nephre on 2006-09-03
Check this thread:

[http://ubuntuforums.org/showthread.php?t=249818]("http://ubuntuforums.org/showthread.php?t=249818")

---

