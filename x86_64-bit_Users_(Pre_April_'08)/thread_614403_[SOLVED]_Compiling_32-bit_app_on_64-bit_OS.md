---
title: "[SOLVED] Compiling 32-bit app on 64-bit OS"
date: 2007-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by moparisthebest on 2007-11-15
I have looked around a lot on google, and seem to be doing this the correct way but gcc is throwing a fit, any help would be appreciated.

program(hello.c):
```

#include<stdio.h>
main()
{
printf("Hello!\n");
}

```

command:
```

mopar@killer-linux:~/projects/c++/32v64test$ gcc -m32 hello.c -o hello32
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.1/libgcc.a when searching for -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.1/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
collect2: ld returned 1 exit status

```

I have also tried '-L/usr/lib32' with the same effect.

I have all the packages that should be required as well:
```
mopar@killer-linux:~/projects/c++/32v64test$ sudo apt-get install ia32-libs lib32gcc1 lib32stdc++6 libc6-dev-i386 gcc-multilib
Reading package lists... Done
Building dependency tree
Reading state information... Done
ia32-libs is already the newest version.
lib32gcc1 is already the newest version.
lib32stdc++6 is already the newest version.
libc6-dev-i386 is already the newest version.
gcc-multilib is already the newest version.
```

I am running a Gutsy that has been upgraded from feisty, edgy and dapper.  If you need anything else ask and I will answer, thanks for the help.

edit:

Of course right after I post a thread I solve the problem myself...

Apt in it's infinite wisdom installed the gcc-multilib for gcc 4.1 when I am using gcc 4.2, so installing 'gcc-4.2-multilib' fixed the problem, thanks apt!

---

