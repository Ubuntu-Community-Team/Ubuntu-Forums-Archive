---
title: "Compile 32bit on 64bit"
date: 2007-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by steven43126 on 2007-11-11
How do i compile software for 32bit on a 64bit machine? Trying to compile i get the following error.

/lib/libc.so.6: file not recognized: File format not recognized
collect2: ld returned 1 exit status
make[4]: *** [libgcc_s.so] Error 1
make[4]: *** Waiting for unfinished jobs....
/tools_i486/x86_64-unknown-linux-gnu/bin/ld: skipping incompatible /usr/lib/../lib/libc.so when searching for -lc
/tools_i486/x86_64-unknown-linux-gnu/bin/ld: skipping incompatible /usr/lib/../lib/libc.a when searching for -lc
/tools_i486/x86_64-unknown-linux-gnu/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/tools_i486/x86_64-unknown-linux-gnu/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/tools_i486/x86_64-unknown-linux-gnu/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
make[4]: *** [32/libgcc_s.so] Error 1
make[4]: Leaving directory `/home/steven/IPCOP/ipcop/ipcop/trunk/build_i486/ipcop/usr/src/gcc-build/gcc'
make[3]: *** [stmp-multilib] Error 2
make[3]: Leaving directory `/home/steven/IPCOP/ipcop/ipcop/trunk/build_i486/ipcop/usr/src/gcc-build/gcc'
make[2]: *** [stage1_build] Error 2
make[2]: Leaving directory `/home/steven/IPCOP/ipcop/ipcop/trunk/build_i486/ipcop/usr/src/gcc-build/gcc'
make[1]: *** [bootstrap] Error 2
make[1]: Leaving directory `/home/steven/IPCOP/ipcop/ipcop/trunk/build_i486/ipcop/usr/src/gcc-build'
make: *** [/home/steven/IPCOP/ipcop/ipcop/trunk/log_i486/01_toolchain/gcc-4.1.2-pass1]

I'm guessing thats because the compile is trying to include a 64bit lib ??

Any help appreciated.

Steve.

---

### Post by John.Michael.Kane on 2007-11-11
From I have read on compiling apps. You be able to simply pass the -m64 or -m32 commands

Depending on how you plan to do it you would use the -m32 and -m64 option. These options generate code for 32-bit or 64-bit environments.

The 32-bit environment should set int, long and pointer to 32 bits and generate code that runs on any i386 system.

The 64-bit environment should set int to 32 bits and long and pointer to 64 bits and generate code for AMD&#8217;s x86-64 architecture.

You can pass -m64 or -m32 like so.
For 32 bit version:
```
gcc -m32 -o output32 foo.c
```
For 64 bit version :
```
gcc -m64 -o output64 foo.c
```

The other method would be to set up a 32-bit chroot environment 
[Setting up 32-bit chroot environment ]("http://jrblevin.freeshell.org/linux/chroot/")

Hope this helps.

---

