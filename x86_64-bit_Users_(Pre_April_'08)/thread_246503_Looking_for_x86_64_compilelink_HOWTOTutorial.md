---
title: "Looking for x86_64 compile/link HOWTO/Tutorial"
date: 2006-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by mw888 on 2006-08-29
I'm new to the Linux x86_64 world but not new to Linux (been installing and using it since the 1.1 days) and I'm looking for a HOWTO/tutorial that will help explain how things operate in an Ubuntu/Debian x86_64 install (6.06.1 x86_64 Server in my case).

Here are the types of questions I'm hoping to get answered:

If I compile something with gcc is it going to be 64-bit by default or do I still need to pass in the appropriate flag(s) (e.g. march=k 8 [no space, that's to fix the smiley])?

How do I tell if something is compiled for 64-bit or not, particularly if it's statically compiled?

Why do I have a /lib and a /lib64 directory?

Also I don't know if this is a bug or not but when I tried to run ldd on a statically compiled program (a copy of zsh compiled from source) I got this error:

```

root@ubuntu:/usr/local/src/zsh-4.3.2/Src# ldd zsh
/usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory
ldd: /lib/ld-linux.so.2 exited with unknown exit code (127)
```
I had to install the 32-bit libraries to get that error to go away (and now I have a /lib32 directory, yeah!). Why would ldd require that, or is that just a bug?

---

### Post by rplantz on 2006-08-29
> **mw888 said:**
> 
If I compile something with gcc is it going to be 64-bit by default or do I still need to pass in the appropriate flag(s) (e.g. march=k 8 [no space, that's to fix the smiley])?


The default is 64-bit. In order to get 32-bit code I have to use the -m32 option when compiling.

> 
How do I tell if something is compiled for 64-bit or not, particularly if it's statically compiled?


```

objdump -f prog_name

```
will tell you.

> 
Why do I have a /lib and a /lib64 directory?


/lib is linked to /lib64. I'm guessing that it's linked to /lib32 in a 32-bit install.

> 
Also I don't know if this is a bug or not but when I tried to run ldd on a statically compiled program (a copy of zsh compiled from source) I got this error:

```

root@ubuntu:/usr/local/src/zsh-4.3.2/Src# ldd zsh
/usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory
ldd: /lib/ld-linux.so.2 exited with unknown exit code (127)
```
I had to install the 32-bit libraries to get that error to go away (and now I have a /lib32 directory, yeah!). Why would ldd require that, or is that just a bug?

I did not try ldd before I installed /lib32, so I don't have an answer.

---

### Post by mw888 on 2006-08-30
> **rplantz said:**
> 
```

objdump -f prog_name

```
will tell you.

Thanks, that helps a lot.

> 
/lib is linked to /lib64. I'm guessing that it's linked to /lib32 in a 32-bit install.

Yeah I'm just curious why it needs both. E.g. when you run ldd you might get something like:
```

root@ubuntu:/bin# ldd grep
        libc.so.6 => /lib/libc.so.6 (0x00002aaaaabc2000)
        /lib64/ld-linux-x86-64.so.2 (0x00002aaaaaaab000)

```
so grep is referencing /lib instead of /lib64 even though it's x86_64 but for some reason the dynamic linker is referenced out of /lib64.

---

