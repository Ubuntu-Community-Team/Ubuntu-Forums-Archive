---
title: "compiling for 64-bit app"
date: 2008-09-04
forum: x86 64-bit Users
---

### Post by wcochran66 on 2008-09-04
I want gcc to generate 64-bit code so I use the -m64 and
get the following error:

$ cc -c -m64 -S t.c
In file included from /usr/include/features.h:354,
                 from /usr/include/stdio.h:28,
                 from t.c:1:
/usr/include/gnu/stubs.h:9:27: error: gnu/stubs-64.h: No such file or directory

I can see that 64-bit code is in the assembler output t.s:

$ more t.s
...
movq	$1234, -8(%rbp)
...

but the above error prevents me from going further.
Indeed there is no /usr/include/gnu/stubs-64.h file (there is a stubs-32.h however).

What magic do I need to get gcc to build 64-bit apps?
It on a x86-64 machine (Ubuntu on an iMac actually) running a 32-bit kernel.

Thanks for any help.

--w

---

### Post by kjohansen on 2008-09-04
```

sudo apt-get install libc6-dev-amd64 

```


A 64 bit gcc should default to 64 making the flag not necessary but since you are on 32 so you still need the flag and the package i listed.

---

### Post by kjohansen on 2008-09-04
just for completeness if you are trying to do the reverse of this post, that is to compile 32 bit from 64 bit you need to do 
```

sudo apt-get install libc6-dev-i386

```

and use the 32 bit flag

---

### Post by wcochran66 on 2008-09-05
Thanks -- I am now clearly generating 64-bit code
without the previous error:

$ gcc -c -m64 -S t.c
$ more t.s
...
	movq	$1234, -8(%rbp)
...

But now linking is the problem:

$ gcc -m64 t.c -o t
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.2.3/libg
cc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status

Are my old lib's now incompatble? 
What do I do next?

---

### Post by Kilz on 2008-09-05
> **wcochran66 said:**
> Thanks -- I am now clearly generating 64-bit code
without the previous error:

$ gcc -c -m64 -S t.c
$ more t.s
...
	movq	$1234, -8(%rbp)
...

But now linking is the problem:

$ gcc -m64 t.c -o t
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.2.3/libg
cc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status

Are my old lib's now incompatble? 
What do I do next?

If you are on a 32bit machine you only have 32bit libraries. The 64bit application you are compiling needs 64bit libraries. 32bit distros do not have a place to put 64bit libraries and if you did force install them it may overwrite 32bit libraries your system needs.

---

### Post by wcochran66 on 2008-09-05
I don't buy that. There clearly are seperate namespaces
for 32-bit and 64-bit libraries:

$ ls -l /usr/lib/libc.a
-rw-r--r-- 1 root root 2906282 2008-04-04 16:38 /usr/lib/libc.a
$ ls -l /usr/lib64/libc.a
-rw-r--r-- 1 root root 4397596 2008-04-04 16:39 /usr/lib64/libc.a

Somehow the -m64 flag should make its way from gcc to ld to tell it which
to use.

---

### Post by wcochran66 on 2008-09-05
Yes, installing gcc-multilib solved the ld problem:

$ apt-get install gcc-multilib

Now, I am up against the hard, cold fact that a 32-bit kernel
does not want to load a 64-bit app:

$ ./t
bash: ./t: cannot execute binary file

I was under the illusion that a 32-bit kernel on a 64-bit CPU
could still load and execute a 64-bit program (works under OS X on the same
machine). Is this true?

---

### Post by jespdj on 2008-09-05
> **wcochran66 said:**
> I was under the illusion that a 32-bit kernel on a 64-bit CPU
could still load and execute a 64-bit program (works under OS X on the same
machine). Is this true?
As far as I know, no you cannot run 64-bit programs on a 32-bit Linux kernel. The reverse (running 32-bit apps on 64-bit Linux) does work.

---

