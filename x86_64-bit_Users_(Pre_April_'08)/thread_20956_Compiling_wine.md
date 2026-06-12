---
title: "Compiling wine?"
date: 2005-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by AndersAA on 2005-03-19
I wanna get cvs wine installed, so I'm trying to cross compile it.

did

export CC='gcc-3.4 -m32'
export CXX='g++-3.4 -m32'

and it'll start to compile, but stop on 

/usr/bin/ld: skipping incompatible /usr/X11R6/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/X11R6/lib/libXext.a when searching for -lXext

because there seems to be no 32bit libs for those available.  Anyone know how to get em?

---

### Post by wmcbrine on 2005-03-20
Just add -L/usr/X11R6/lib32/ to the link line in the Makefile (or, as with the compiler, define an appropriate environment variable if available).

I can't tell you if this will get you WINE (I haven't tried that yet), but at least it should find the 32-bit versions of the X libs.

---

### Post by AndersAA on 2005-03-24
nope :/, doesn't work, /etc/ld.so.conf also has /usr/X11R6/lib32 already.


if I do :

cd /usr/X11R6/lib32
ln -s  libXext.so.6 libXext.so
ln -s libX11.so.6 libX11.so


then compile that line with -L/usr/X11R6/lib32 I get:

/usr/bin/ld: skipping incompatible /usr/X11R6/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/X11R6/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/X11R6/lib/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible /usr/X11R6/lib/libX11.a when searching for -lX11

---

### Post by wmcbrine on 2005-03-28
OK, I got WINE compiled, but it doesn't work. It just exits immediately with no error message. Googling on this, I found some people saying that recent versions of WINE didn't like recent versions of the Linux kernel (maybe just the AMD64 kernel), especially 2.6.10. No details. Anyway, just for amusement value, here's what I did to get it built:

1. Set CC like you did.
2. ./configure --x-libraries=/usr/X11R6/lib32
3. Make .so links for all the libraries in that dir.
4. The tricky one -- eventually you'll get an error about SYS_sigaction. (Sorry, I forget the file, and I deleted my WINE source in a fit of pique.) If you change this to SYS_rt_sigaction, it will compile. I'm not sure this is the *correct* solution, but it's what someone else on the Net suggested.

This gets the binary built, but it does nothing, at least on my system.

Now I'm trying to chroot my old 32-bit installation and run WINE from there. So far, this is more promising; but it stops with a complaint that it can't access the display. I've tried "xhost +", and changing DISPLAY to point explicitly to the hostname, with no effect.

And if I get that to work, my last reason for booting to 32-bit Linux will be... to run DOSEmu. :-/  (DOSBox isn't quite cutting it; for one thing, pkunzip finds nonexistent errors in every file (all verified OK). I tried running it from the chroot (I don't get this problem in the 32-bit system), but it just hung.)

---

### Post by AndersAA on 2005-03-28
I was just going to post the same thing now ;)


export CC='gcc-3.4 -m32'
export CXX='g++-3.4 -m32'

./configure --x-libraries=/usr/X11R6/lib32 --disable-arts LD='ld -m elf_i386'
make depend && make

the file to change is dlls/ntdll/signal_i386.c, SYS_sigaction -> SYS_rt_sigaction


need the disable-arts cuz I have kubuntu installed aswell.

---

### Post by AndersAA on 2005-03-28
strace on wine executable doing nothing:

#LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib strace wine
```

mprotect(0x556e8000, 4096, PROT_NONE)   = 0
clone(child_stack=0x55ee7b48, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID|CLONE_DETACHED, parent_tidptr=0x55ee7bf8, tls=0xffffd820, child_tidptr=0x55ee7bf8) = 29509
futex(0x55ee7bf8, FUTEX_WAIT, 29509, ptrace: umoven: Input/output error
{...}) = 0
execve("/usr/local/bin/wine-preloader", [umovestr: Input/output error
0x804a0600804a080, umovestr: Input/output error
0x20f5100000000], [/* 33 vars */]) = 0
link("", "")                            = -1 ENOENT (No such file or directory)
link("", "")                            = -1 ENOENT (No such file or directory)
link("", "")                            = -1 ENOENT (No such file or directory)
fork()                                  = 29510
--- SIGCHLD (Child exited) @ 0 (0) ---
setup()                                 = -1 EINTR (Interrupted system call)
_exit(2)                                = ?

```

---

### Post by wmcbrine on 2005-03-29
[QUOTE=wmcbrine]Now I'm trying to chroot my old 32-bit installation and run WINE from there. So far, this is more promising; but it stops with a complaint that it can't access the display.[/quote]
OK, I got this sorted -- I just had to mount --bind /tmp /oldroot/tmp.

The 32-bit DOSBox works as well, and doesn't have the pkunzip problem. Also Mozilla w/ Flash and Java... the only thing I'm missing is sound. (None of the chroot apps is making sound. I probably have to do something with /dev, but mount --bind /dev /oldroot/dev isn't it.) But I'm getting off-topic for this thread.

---

