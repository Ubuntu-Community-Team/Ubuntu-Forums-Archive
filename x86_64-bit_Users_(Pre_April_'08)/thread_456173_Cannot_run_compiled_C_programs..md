---
title: "Cannot run compiled C programs."
date: 2007-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by derrekito on 2007-05-27
```

#include <stdio.h>

main()
{
        printf ("Hello World!\n");
	return(0);
}

```

simple hello world.

I do:

```

gcc -Wall  -c hello.c -o hello
./hello

```

it doesnt work.  I tried using IDEs such as Geany, after compiling and pressing F5 nothing happens.  running through console I get a permission denied, then I sudo ./hello and I get a command not found (I am in the correct directory).

I have no problems with my 32-bit feisty running on my laptop, so thats why I am posting here.

---

### Post by Vixis on 2007-05-27
Try this:
 gcc hello.c -o hello

From 'man gcc':
 -c  Compile or assemble the source files, but do not link.  The linking stage simply is not done.

---

### Post by derrekito on 2007-05-27
running the above program as you suggested yeilds:

```

derrekito@derrekito-desktop:~/Desktop$ gcc hello.c -o hello_world
derrekito@derrekito-desktop:~/Desktop$ 

```

I get no output.


EDIT:

I'm an idiot it works...


So what exactly was wrong with my origional approach to compilining and running?  I'm a little lost here...

---

### Post by Vixis on 2007-05-28
The -c option tells gcc to compile the code into object code and to skip the assembly and linking stages of the compile.

---

### Post by derrekito on 2007-05-28
thanks a bunch!

---

### Post by Geneset on 2008-03-02
I am having a similar issue with more complex code, but it appears that any code produces the same result.
```
gcc -Wall proto0.c -o proto0
./proto0
bash: ./proto0: Permission denied

```

and just to chk, my ls -l
```
total 348
-rwxr-xr-x 1 user user 35650 2008-03-01 21:59 a.out
drwxr-xr-x 4 user user  4096 2006-01-08 16:24 c_count-7.11
-rw-r--r-- 1 user user 79060 2008-02-09 22:51 c_count.tar.gz
drwxr-xr-x 2 user user  4096 2008-03-01 21:53 lcc
-rw-r--r-- 1 user user  1723 2008-02-27 01:17 my.h
-rwxr-xr-x 1 user user  7638 2008-02-09 22:31 option
-rwxr--r-- 1 user user   734 2008-03-01 18:07 option.c
-rw-r--r-- 1 user user   369 2008-02-26 19:13 output
-rwxr-xr-x 1 user user 35650 2008-03-02 19:15 proto0
-rw-r--r-- 1 user user 12809 2008-03-01 21:53 proto0.c
-rw-r--r-- 1 user user 12802 2008-03-01 21:52 proto0.~c
-rw-r--r-- 1 user user 30272 2008-03-01 18:04 proto0.o
-rw-r--r-- 1 user user   886 2008-03-01 21:55 proto0.prj
-rwxr-xr-x 1 user user 35160 2008-02-26 18:37 proto1
-rw-r--r-- 1 user user 11570 2008-02-26 18:24 proto1.c
-rwxr-xr-x 1 user user 35726 2008-02-27 01:24 proto2
-rw-r--r-- 1 user user 10117 2008-02-27 01:17 proto2.c

```

Any ideas?

---

### Post by derrekito on 2008-03-02
Let me know if this works for you:

```

gcc proto0.c 
./a.out

```

Or instead:

It looks like you need to set you binary access rights.  A lazy fix is to use nautilus to browse to that file, the right click on it, go to properties.  Where the permissions are enable the check box that calls for executable rights.

---

### Post by Geneset on 2008-03-02
```
bash: ./a.out: Permission denied

```

Same applies nomatter what permissions i try on both the file and directory through both nautilus and even chmod 777 a.out

---

### Post by derrekito on 2008-03-02
not that I would want you to do it, but have you tried ```
sudo ./a.out
``` ??

---

### Post by Geneset on 2008-03-02
False alarm, i recently re-arranged my entire development setup and I didnt have the new partitions mounted as exec in /etc/fstab.

Duh. lol. Thanks for all the fish

---

### Post by cprofitt on 2008-03-03
Man... some good advice in here... when I finally get to development work on my Linux boxes I hope that I will remember this stuff.

---

