---
title: "Where to get Amay 10.0.1?"
date: 2008-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by vixensjlin on 2008-03-29
Hi there,

I was trying to get [Amaya 10.0.1]("http://www.w3.org/Amaya/User/BinDist.html") and there's no AMD64 binaries available.  I tried Amaya 9.54 which is available in AMD64 collection, but the table editing of 9,54 is really worse than 10.0.1.  The only AMD64 binary of 10.0.1 was [Mandriva]("http://fr2.rpmfind.net//linux/RPM/mandriva/devel/cooker/x86_64/media/contrib/release/amaya-10.0-1mdv2008.1.x86_64.html"), but I doubt it can work.

I then download the Amaya 10.0.1 source to compile by myself but the compilation was error.  Can anybody know how to get Amaya 10.0.1 running on my AMD64 Gutsy?  Thanks!

PS. the error message of the compilation:
gcc -c -I../../include -I../../src/mesa -I../../src/mesa/main -I../../src/mesa/glapi -I../../src/mesa/math -I../../src/mesa/tnl -I../../src/mesa/shader -I../../src/mesa/shader/grammar -I../../src/mesa/shader/slang -I../../src/mesa/swrast -I../../src/mesa/swrast_setup -Wall -Wmissing-prototypes -O3 -g -fPIC  -D_POSIX_SOURCE -D_POSIX_C_SOURCE=199309L -D_SVID_SOURCE -D_BSD_SOURCE -D_GNU_SOURCE -DPTHREADS -DUSE_XSHM -DHAVE_POSIX_MEMALIGN -DUSE_X86_ASM -DUSE_MMX_ASM -DUSE_3DNOW_ASM -DUSE_SSE_ASM -I/usr/X11R6/include -std=c99 -ffast-math  x86/common_x86_asm.S -o x86/common_x86_asm.o
x86/common_x86_asm.S: Assembler messages:
x86/common_x86_asm.S:54: Error: suffix or operands invalid for `pushf'
x86/common_x86_asm.S:55: Error: suffix or operands invalid for `pop'
x86/common_x86_asm.S:58: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:59: Error: suffix or operands invalid for `popf'
x86/common_x86_asm.S:60: Error: suffix or operands invalid for `pushf'
x86/common_x86_asm.S:61: Error: suffix or operands invalid for `pop'
x86/common_x86_asm.S:77: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:78: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:91: Error: suffix or operands invalid for `pop'
x86/common_x86_asm.S:92: Error: suffix or operands invalid for `pop'
x86/common_x86_asm.S:101: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:105: Error: suffix or operands invalid for `pop'
x86/common_x86_asm.S:114: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:119: Error: suffix or operands invalid for `pop'
x86/common_x86_asm.S:128: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:133: Error: suffix or operands invalid for `pop'
x86/common_x86_asm.S:142: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:147: Error: suffix or operands invalid for `pop'
x86/common_x86_asm.S:182: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:198: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:199: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:200: Error: suffix or operands invalid for `push'
x86/common_x86_asm.S:201: Error: suffix or operands invalid for `push'
make[4]: *** [x86/common_x86_asm.o] Error 1
make[4]: Leaving directory `/home/sjlin/Amaya10.0/Amaya/linux/Mesa/src/mesa'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/home/sjlin/Amaya10.0/Amaya/linux/Mesa/src/mesa'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/sjlin/Amaya10.0/Amaya/linux/Mesa/src'
make[1]: *** [default] Error 1
make[1]: Leaving directory `/home/sjlin/Amaya10.0/Amaya/linux/Mesa'
make: *** [gl] Error 2

---

### Post by lduperval on 2008-04-05
To compile it, I did this on Feisty:

% cp Mesa/configs/linux-dri-x86-64 current
% sudo make (in the object directory)

I also had a problem compiling in the batch directory, so I copied everything from the batch directory to the obj/batch directory. 

Whenever I ran make in the batch directory, I had an errror. So I ended up doping all of those commands manually. I did it like this:

% export THOTDIR=../..
% make
# an error appeared
% ../bin/grm APP
% make
# an error occured
% ../bin/grm .... (here I put the value that appears in the error message)

It is possible that you need to be root to compile it. I kept seeing some "permissin denied" errors when I compiled and in order to finish the complete the build, I had to do

sudo make

even though I was compiling in my home directory.

Go figure.

Hope that helps,

L

---

### Post by lduperval on 2008-04-05
Simplest way yet: remove the gl tag from the default: target of the main file. This will build amaya without trying to build Mesa. As long as you have Mesa installed on your system, it will work correctly.

You may need to do "sudo make" from the toplevel directory.

L

---

### Post by plutus on 2008-05-21
I had the same problem on my AMD64 system.

**Solution:**
Overwrite *current* in ~/Amaya10.0/amaya/linux/Mesa/configs/ with *linux-x86-64-static*.

More information can be found on: [http://www.w3.org/Amaya/User/Autoconf.html](http://www.w3.org/Amaya/User/Autoconf.html)

---

