---
title: "compiling 32-bit code on edgy 64?"
date: 2006-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by The Warlock on 2006-10-27
I need to be able to code in normal IA32 asm for one of my classes. I recently updated to 64-bit edgy. What's the gcc flag to compile for 32-bit? Or should I run everything under linux32? Or what?

---

### Post by Mongoose on 2006-10-27
You could cross compile, but having a full 32bit chroot is very nice for testing too.  If you really need it you can install VMs for various OS and distros.  I think that's more of outside a school project however.   ;)

I have XP (vmware), OS X (vmware), and an ubuntu LTS chroot to test the application I'm developing from ubuntu on amd64.  This way I only need one machine on my desk.  If I have to run native ( which is very rare ) I fire up another native box or use eSATA multiboot.  Welcome to cross platform development!

---

### Post by The Warlock on 2006-10-27
> **Mongoose said:**
> You could cross compile, but having a full 32bit chroot is very nice for testing too.  If you really need it you can install VMs for various OS and distros.  I think that's more of outside a school project however.   ;)

I have XP (vmware), OS X (vmware), and an ubuntu LTS chroot to test the application I'm developing from ubuntu on amd64.  This way I only need one machine on my desk.  If I have to run native ( which is very rare ) I fire up another native box or use eSATA multiboot.  Welcome to cross platform development!

Heh, well, this isn't that advanced a class, just some basic asm (for now). 

Evidently the package I didn't realize I needed to install was ia32-libs. Now the -m32 flag works instead of spitting errors.

---

### Post by kuja on 2006-10-27
Maybe the -m32 option?
> -m32 -m64
Generate code for 32-bit or 64-bit environments of Darwin and SVR4 targets (including GNU/Linux). The 32-bit environment sets int, long and pointer to 32 bits and generates code that runs on any PowerPC variant.  The 64-bit environment sets int to 32 bits and long and pointer to 64 bits, and generates code for PowerPC64, as for -mpowerpc64.

---

### Post by The Warlock on 2006-10-27
> **kuja said:**
> Maybe the -m32 option?

I was doing that, but if you don't have the ia32-libs package installed, it won't work.

---

### Post by kuja on 2006-10-27
Then why not install the ia32-libs package?

---

### Post by rplantz on 2006-10-27
I have ia32-libs installed. (I also resinstalled it, just to make sure.)

Now on a simple printf("hello world.\n") program I get the error:
```

bob@ubuntu:~/programing$ gcc -m32 helloworld.c 
In file included from /usr/include/features.h:346,
                 from /usr/include/stdio.h:28,
                 from helloworld.c:1:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
bob@ubuntu:~/programing$ 

```

This used to work for me under both Dapper and Hoary. I used to have ia32-libs-dev also installed under Hoary. I do not recall if I needed to install it under Dapper.

From the error message, it looks like this is what I need. However, it is not in the repositories. And when I tried to install ia32-libs-dev_1.4_amd64.deb, it would not go because it requires ia32-libs 1.4, but edgy installs ia32-libs 1.5ubunutu5.

Edit: I just filed a bug report on this, #68859

---

### Post by The Warlock on 2006-10-28
> **kuja said:**
> Then why not install the ia32-libs package?

Because I didn't realize I needed it. That's... um... what I was asking in this thread.

---

### Post by rplantz on 2006-10-28
> **The Warlock said:**
> I need to be able to code in normal IA32 asm for one of my classes.

When it's working correctly, if you write gnu assembly language, you should be able to do
```

as --gstabs --32 -o myProg.o myProg.s
as --gstabs --32 -o sub.o sub.s

```
to assemble your source code and produce object (.o) files. Then do
```

gcc -m32 -o myProg myProg.o sub.o

```
to link them together and produce the executable program, myProg.

This assumes that your program starts with a main function. Using this technique, you can also use C I/O routines (e.g., printf, scanf). The advantage of using gcc for the linking phase is that it automatically links in the required libraries. Unfortunately, this seems to be broken in edgy. :(

---

### Post by rplantz on 2006-10-29
> **The Warlock said:**
> Because I didn't realize I needed it. That's... um... what I was asking in this thread.

I figured out the other package that needs to be installed: libc6-dev-i386.


Edit: My earlier message showed three packages. Turns out that the only package you need is libc6-dev-i386.

---

