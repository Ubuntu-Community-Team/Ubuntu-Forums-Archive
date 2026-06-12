---
title: "[SOLVED] Ubuntu Hardy: gcc problem with Vortex86SX (also found on eBox 2300SX)"
date: 2008-06-26
forum: x86 64-bit Users
---

### Post by islambadr on 2008-06-26
Hello there!

I am having problems compiling C programs for the Vortex86SX target (claims to be 100% i486 compatible). The problem is that all the user land programs compiled using gcc just freezes when I try to execute them on the target hardware. The system does not freeze however, as keyboard key-presses are echoed on the screen. The kernel does not panic.

```
gcc --version
gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
```

I compiled a simple helloworld:

```
$gcc -march=i486 -m32 -O2 --static hello.c -o hello_32
$ file ./hello_32
./hello_32: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, statically linked, not stripped
```

I managed to compile a working Linux kernel and it is running successfully on the target. The problems comes when I compile any user land programs. Passing the compiled programs as rdinit=/bin/hello_32 (I'm using initramfs), the system freezes on the target with no error messages!! Note that everything works PERFECTLY on qemu and on my own host!

I tried the root filesystem available from [ftp://download@ftp.dmp.com.tw/os-xlinux/xlr54-rootfs.tar.gz]("ftp://download@ftp.dmp.com.tw/os-xlinux/xlr54-rootfs.tar.gz") and packaged it into an initramfs image. It booted successfully on the target hardware with no errors.

Can anybody guide me on what's wrong?? Is it a bug with gcc 4.2 or I am missing some other compiler flags???

Thanks a lot

-Islam

---

### Post by islambadr on 2008-07-01
Hi there!

I did further investigations on this. I _injected_ my statically compiled hello_32 program into the root filesystem available from [ftp://download@ftp.dmp.com.tw/os-xlinux/xlr54-rootfs.tar.gz]("ftp://download@ftp.dmp.com.tw/os-xlinux/xlr54-rootfs.tar.gz"). Then, after successfully booting my kernel with the aforementioned rfs (as initramfs image), I tried to execute the _static_ hello_32 binary. It should produce the output "hello", however, I got the following error:

```
# hello_32
Illegal Instruction
```

For further debugging, I compiled the hello_32 program on a virtual machine with Debian Etch gcc-4.1 32-bit compiler with glibc version 2.3.6. It was also compiled as a static binary. I also injected it into the aforementioned root filesystem, and executed it. It executes successfully:

```
# hello_32
hello#
```

So, basically I think the culprit is glibc version 2.7-10 which is the library to be used with gcc-4.2. I think the library is compiled with optimization instructions not suitable to run on i486 architectures, or to be more precise, not suitable to run on the Vortex86SX chip :'(

I am attaching another snapshot illustrating the "Illegal Instruction" error.

Should I file a new bug on the build flags of glibc 2.7?? or I need to do further debugging first?

-Islam

---

### Post by Cappy on 2008-07-01
You should try posting this in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") section.

---

### Post by Yellow Pasque on 2008-07-01
Try excluding the -O2 flag or changing to -O0 (optimize for file size). You might also try sticking to the i386 standard.
```
$gcc -march=i486 -m32 **-O2** --static hello.c -o hello_32
```
A technical explanation of optimizing flags: [http://www.linuxjournal.com/article/7269](http://www.linuxjournal.com/article/7269)

---

### Post by islambadr on 2008-07-02
This bug is gonna drive me crazy !!!

Now, compiling the same hello world program as static --> works fine
Compiling it as shared --> Illegal Instruction bug



My system is:

```
$gcc --version
gcc (GCC) 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

$ apt-cache show libc6 | grep Version
Version: 2.3.6.ds1-13etch5

$uname -a
Linux debian 2.6.18-6-686 #1 SMP Sun Feb 10 22:11:31 UTC 2008 i686 GNU/Linux
```

The output on the Vortex86SX target:

```
#/bin/hello_32
hello#
#/bin/hello_32_shared
Illegal Instruction
#

```

Notice that I had to compile busybox as a static binary to be able to boot in this scenario!!

How can I trace this issue further? The target architecture is [Vortex86SX]("http://www.dmp.com.tw/tech/Vortex86SX/")

---

### Post by islambadr on 2008-07-02
SOLVED! the problem lies in the pre-built shared libraries. Seems that new versions of Ubuntu and Debian binaries are less compatible with i486 architectures. I have changed the shared libraries binaries in the root filesystem with the ones found in Debian oldstable (sarge). Installing the shared libraries found in [this package]("http://packages.debian.org/sarge/libc6") into my root filesystem solved all the problems =D No more "Illegal Instruction" popping up every now and then... I even managed to run Qt/Embedded 4.4.0 examples on this board, though the performance is really horrible :S All the examples run extremely slow on this board. It seems that performance of the Linux framebuffer driver on this board is extremely bad, maybe due to memory access bottleneck??

Does anybody think this should be filed as a bug on the build flags of libraries in modern Linux distributions? Basically the Linux system should run equally well on most x86 boards, with no "Illegal Instruction" bugs!!


PS: This is the result of running my current working libc:

```
$/lib/libc.so.6
GNU C Library stable release version 2.3.2, by Roland McGrath et al.
Copyright (C) 2003 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 3.3.5 (Debian 1:3.3.5-13).
Compiled on a Linux 2.6.0-test7 system on 2007-03-05.
Available extensions:
        GNU libio by Per Bothner
        crypt add-on version 2.1 by Michael Glad and others
        linuxthreads-0.10 by Xavier Leroy
        BIND-8.2.3-T5B
        libthread_db work sponsored by Alpha Processor Inc
        NIS(YP)/NIS+ NSS modules 0.19 by Thorsten Kukuk
Thread-local storage support included.
Report bugs using the `glibcbug' script to <bugs@gnu.org>.

```

---

### Post by islambadr on 2008-07-15
I totally understand the problem an its solution by now! I am sharing it with you here:

The multilib package on 64-bit systems contains C library that is optimized for i686. The purpose of this library is NOT cross-compiling to 32-bit systems but rather to allow 64-bit users to run 32-bit applications happily!

Also, even on 32-bit environments, there is a libc6-i686 package which contains libraries optimized for i686 systems. So, if this package is installed, you have to compile using the -marach=i486 flag to force the linker to pick the 486 version of the C libraries and not the 686 version.

In a nutshell, you MUST have a chrooted 32-bit environment to cross-compile your applications for i486! Also, you must use the -march=i486 flag if the libc6-i686 package is installed.

Hope that helps...

-Islam

---

### Post by Yellow Pasque on 2008-07-15
> The purpose of this library is NOT cross-compiling to 32-bit systems but rather to allow 64-bit users to run 32-bit applications happily!

I don't think that's how it works. The purpose of gcc-multilib is to support cross-compiling with the -m32 flag. The ia32-libs package "contains runtime libraries for the ia32/i386 architecture, configured for use on an amd64 or ia64 Debian system running a 64-bit kernel."

---

### Post by islambadr on 2008-07-15
> **Temüjin said:**
> I don't think that's how it works. The purpose of gcc-multilib is to support cross-compiling with the -m32 flag. The ia32-libs package "contains runtime libraries for the ia32/i386 architecture, configured for use on an amd64 or ia64 Debian system running a 64-bit kernel."

Yes, I agree. BUT, unfortunately, the c library in the multilib package IS optimized for i686 and NOT for i486. This is because you can safely assume i686 instruction set on all 64-bit platforms from Intel or AMD, AFAIK.

---

