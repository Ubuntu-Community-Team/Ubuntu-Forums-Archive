---
title: "Help me Compile this File!"
date: 2007-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Trippen Out on 2007-04-28
can someone please help me with this

[http://paste.ubuntu-nl.org/18176/](http://paste.ubuntu-nl.org/18176/)

useing fiesty fawn 7.04 64bit


	

trippen@phasedc2d:~/Desktop/libprojectM$ make
make  all-recursive
make[1]: Entering directory `/home/trippen/Desktop/libprojectM'
Making all in src
make[2]: Entering directory `/home/trippen/Desktop/libprojectM/src'
/bin/sh ../libtool --tag=CXX --mode=link g++ -DLINUX -D__CPLUSPLUS -pthread -I/usr/include/FTGL -I/usr/include/freetype2   -g -O2   -o libprojectM.la -rpath /usr/local/lib -version-info 0:0:0 PCM.lo beat_detect.lo browser.lo builtin_funcs.lo console_interface.lo custom_shape.lo custom_wave.lo editor.lo eval.lo fftsg.lo func.lo glConsole.lo init_cond.lo menu.lo param.lo parser.lo pbuffer.lo per_frame_eqn.lo per_pixel_eqn.lo preset.lo projectM.lo splaytree.lo timer.lo tree_types.lo wipemalloc.lo -lGL  -lm -lGLU -lGL -lfreetype -lz -lftgl   
g++ -shared -nostdlib /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.1.2/crtbeginS.o  .libs/PCM.o .libs/beat_detect.o .libs/browser.o .libs/builtin_funcs.o .libs/console_interface.o .libs/custom_shape.o .libs/custom_wave.o .libs/editor.o .libs/eval.o .libs/fftsg.o .libs/func.o .libs/glConsole.o .libs/init_cond.o .libs/menu.o .libs/param.o .libs/parser.o .libs/pbuffer.o .libs/per_frame_eqn.o .libs/per_pixel_eqn.o .libs/preset.o .libs/projectM.o .libs/splaytree.o .libs/timer.o .libs/tree_types.o .libs/wipemalloc.o  -Wl,--rpath -Wl,/usr/lib -Wl,--rpath -Wl,/usr/lib -lGLU -lGL /usr/lib/libfreetype.so -lz -lftgl -L/usr/lib/gcc/x86_64-linux-gnu/4.1.2 -L/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64 -L/lib/../lib64 -L/usr/lib/../lib64 -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/x86_64-linux-gnu/4.1.2/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/crtn.o  -pthread -Wl,-soname -Wl,libprojectM.so.0 -o .libs/libprojectM.so.0.0.0
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libprojectM.la] Error 1
make[2]: Leaving directory `/home/trippen/Desktop/libprojectM/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/trippen/Desktop/libprojectM'
make: *** [all] Error 2
trippen@phasedc2d:~/Desktop/libprojectM$

---

### Post by SendDerek on 2007-04-29
It sounds silly, but have you tried to run as sudo?

Whenever I get a message that looks similar, I usually just run "sudo make" and it compiles just fine.

---

### Post by Trippen Out on 2007-04-29
yes i have tried that..  and no it didnt work..

---

### Post by faddat on 2007-04-30
Trippen,

I've got the exact same problem!  I'm trying to compile ProjectM.  I followed the directions on what is actually an earlier post of mine looking for help with ProjectM.  

[http://ubuntuforums.org/showthread.php?t=70135&highlight=projectm](http://ubuntuforums.org/showthread.php?t=70135&highlight=projectm)

I think that Feisty is breaking some sort of support for this method, but I really don't know how it broke it.  If you do get ProjectM to compile, please drop a line.  All I need to do is to get 64 bit flash running and ProjectM and my machine will be certifiably pimpin.  

Thanks!

Later.

---

### Post by kuja on 2007-04-30
> **Trippen Out said:**
> 
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC

have you tried this?

---

### Post by Kilz on 2007-04-30
> **kuja said:**
> have you tried this?

That looks like almost the same error that I was getting when trying to compile firefox. [Seems there is a bug in the gcc compiler v4 according to this page I found.]("http://benjamin.smedbergs.us/blog/2006-03-28/gcc-and-visibility-one-step-forward-hit-a-brick-wall/"). Im not sure how you would use the information, but it gives a work around to making firefox build.

---

### Post by skullmunky on 2007-04-30
as the error suggests, you could try recompiling with -fPIC.  i've had that same error wth a bunch of other compiles and -fPIC fixed it.  

i don't know autoconf well enough to do this nicely, so the way i did it was to open the Makefile (for you, that'll be /home/trippen/Desktop/libprojectM/src/Makefile) and edit it by hand.  look for the CFLAGS environment variable and add the -fPIC flag.  then make clean and make again.  

although - since the error is in libfgtl - it's maybe not projectM but libfgtl that has the problem.

---

