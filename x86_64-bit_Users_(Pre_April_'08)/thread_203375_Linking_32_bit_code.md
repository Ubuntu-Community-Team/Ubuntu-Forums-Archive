---
title: "Linking 32 bit code"
date: 2006-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by reddish on 2006-06-25
Hi all,

Linking 32-bit code is causing me some troubles, since the linker doesn't seem to be able to find the lib32 version of the C library. This is on a Kubuntu Dapper Drake system:

$ cat hello_world.c
#include <stdio.h>
int main(void)
{
  puts("hi!");
  return 0;
}
$ gcc -m32 hello_world.c -o hello_world

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

Now I have /lib32/libc.so.6 (which links to libc-2.3.6.so, in the same directory, which is available), but it isn't found by the linker, apparently.

I tried adding /lib32 to /etc/ld/so.conf, and re-running ldconfig, but this did not help.

Any ideas?

---

