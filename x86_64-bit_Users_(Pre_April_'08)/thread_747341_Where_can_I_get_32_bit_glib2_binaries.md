---
title: "Where can I get 32 bit glib2 binaries?"
date: 2008-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by stair314 on 2008-04-06
Is there seriously no binary for glib2? I can't find it in synaptic, and it says that cross-compiling it correctly is harder than ordinary libraries so I would prefer not to try to build it from source myself. Thanks.

---

### Post by Kilz on 2008-04-06
> **stair314 said:**
> Is there seriously no binary for glib2? I can't find it in synaptic, and it says that cross-compiling it correctly is harder than ordinary libraries so I would prefer not to try to build it from source myself. Thanks.
[URL="http://ubuntuforums.org/showthread.php?t=474790"]
Perhaps Getlibs can help you.[/URL]

---

### Post by Cappy on 2008-04-06
Aye,
```
getlibs -p libglib2.0-0
```
once you installed getlibs

---

### Post by stair314 on 2008-04-06
Thanks. Is there a way to check that the getlibs install worked/find out what directory it added the binaries to?

My specific problem is I am trying to build a 32 bit version of OpenCV. I get the error:
/usr/lib/libgthread-2.0.so: could not read symbols: File in wrong format

That file is in 64 bit format, and is supplied by glib2. getlibs agrees with me on that and says it is installing the library:

getlibs -l /usr/lib/libgthread-2.0.so
libgthread-2.0.so: libglib2.0-dev
The following i386 packages will be installed:
libglib2.0-dev
Continue [Y/n]? Y
Downloading ...
Installing libraries ...


But I do not see any new files in /usr/lib that look like a 32 bit version of libgthread and I still get the compiler error. I tried running getlibs with the --ldconfig option but that didn't fix anything either.
Do I need to do any additional commands to expand some package or something like that? Thanks.

---

### Post by stair314 on 2008-04-06
OK, I figured out the 32 bit libraries were going in /usr/lib32, and added that path to the compiler options. It is still trying to read the 64 bit library and dying though. Any idea why?

The /usr/lib32/libgthread-2.0.so was a broken symlink originally but I fixed the symlink and that did not solve the problem.

g++ -shared -nostdlib /usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib32/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.1.3/32/crtbeginS.o  .libs/dummy.o -Wl,--whole-archive ./.libs/lib_highgui.a -Wl,--no-whole-archive  -Wl,--rpath -Wl,/home/ia3n/stair/libs/opencv-1.0.0/cxcore/src/.libs -Wl,--rpath -Wl,/home/ia3n/stair/libs/opencv-1.0.0/cv/src/.libs -Wl,--rpath -Wl,/usr/lib32 -L/home/ia3n/stair/libs/opencv-1.0.0/cxcore/src/.libs -L/usr/lib32 ../../cxcore/src/.libs/libcxcore.so ../../cv/src/.libs/libcv.so /usr/lib/libgthread-2.0.so -L/usr/lib -lrt /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage /usr/lib/libpango-1.0.so /usr/lib/libcairo.so -lX11 -lXfixes /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libglib-2.0.so -lpthread -ldl -L/usr/lib/gcc/x86_64-linux-gnu/4.1.3/32 -L/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib32 -L/lib/../lib32 -L/usr/lib/../lib32 -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/x86_64-linux-gnu/4.1.3/32/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib32/crtn.o  -m32 -pthread -Wl,-soname -Wl,libhighgui.so.1 -o .libs/libhighgui.so.1.0.0
/usr/lib/libgthread-2.0.so: could not read symbols: File in wrong format

---

### Post by Cappy on 2008-04-08
I've never cross compiled so I'm not sure what the correct way to do it is but you may want to just try linking /usr/lib/libgthread-2.0.so to /usr/lib32/libgthread-2.0.so temporarily while you compile. It may work. 

The Programming section would also be a good place to ask.

---

