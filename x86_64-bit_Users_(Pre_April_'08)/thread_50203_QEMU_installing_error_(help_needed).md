---
title: "QEMU installing error (help needed)"
date: 2005-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by yansen on 2005-07-19
hi all, 

newbie asking for help.

I'm trying to install QEMU on my Ubuntu running on AMD64, since i wanna get my DOS application on my Linux.

I've tried to follow instruction found when googling, like :
[http://ubuntu.sun.ac.za/wiki/index.php/QEMU](http://ubuntu.sun.ac.za/wiki/index.php/QEMU) or
[http://www.ubuntuforums.org/showthread.php?p=248747#post248747](http://www.ubuntuforums.org/showthread.php?p=248747#post248747)

but i still got error message like this while i try the "make" command

> root@yansen:/home/yansen/qemu-0.7.0 # make
for d in i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu; do \
make -C $d all || exit 1 ; \
        done
make[1]: Entering directory `/home/yansen/qemu-0.7.0/i386-user'
gcc -g -Wl,-T,/home/yansen/qemu-0.7.0/x86_64.ld -o qemu-i386 elfload.o main.o syscall.o mmap.o signal.o path.o osdep.o thunk.o vm86.o libqemu.a gdbstub.o   -lm
/usr/bin/ld:/home/yansen/qemu-0.7.0/x86_64.ld:62: parse error
collect2: ld returned 1 exit status
make[1]: *** [qemu-i386] Error 1
make[1]: Leaving directory `/home/yansen/qemu-0.7.0/i386-user'
make: *** [all] Error 1

when try ./configure, here is the message :
> root@yansen:/home/yansen/qemu-0.7.0 # ./configure
Install prefix    /usr/local
BIOS directory    /usr/local/share/qemu
binary directory  /usr/local/bin
Manual directory  /usr/local/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /home/yansen/qemu-0.7.0
C compiler        gcc
make              make
host CPU          x86_64
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu
gprof enabled     no
static build      no
SDL support       yes
SDL static link   no
mingw32 support   no
Adlib support     no
FMOD support      no
kqemu support     no

thanks for anyone willing to help,
yansen

---

### Post by negatory on 2005-07-19
I don't really remember but I think I had to run the ./configure script with the "--target-list=x86_64-softmmu" flag...try it like that and post your results here.
Hope that helps...
Pedro Carrico

---

### Post by yansen on 2005-07-20
thanks pedro, it works.. now I can run my Qemu (^_^)

---

### Post by negatory on 2005-07-20
You're welcome...hope you're running other linuxes with that  ;-) 
Pedro Carrico

---

### Post by marwans on 2005-07-30
[QUOTE=yansen]thanks pedro, it works.. now I can run my Qemu (^_^)[/QUOTE]
 Hi,
how do we know whether qemu is already installed? Because everytime i type qemu command (e.g. qemu -boot.....), I always get 'bash: qemu: command not found'.
By the way, I'm running on AMD64, qemu is ver 0.7.1
Thanks for the help...

marwan
- it's good to find other OS -

---

### Post by negatory on 2005-07-30
It's not installed by default,on amd64 you must compile the source.
Grab it from their website and compile it...you can't get it trough apt.
Hope that helps.
Pedro Carrico

---

### Post by marwans on 2005-07-31
Hi Pedro,
Thanks for the info... I also found out that the command is 'qemu-system-x86_64'. No wonder i always got 'command not found' error if I used 'qemu'.

I've installed win2000. But the problem now is that it can't use kqemu. I always get the famous blue error page just after the win2000 banner page. Anybody has any idea why?

marwan
- it's good to find another OS -

---

