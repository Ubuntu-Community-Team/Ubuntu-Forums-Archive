---
title: "compiling -m32"
date: 2008-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2008-03-28
Quote by Killz
> Since you are running 32bit there is no way you could compile 64bit applications. The 32bit verssion limits you to 32bit.
Now, if you were running the 64bit version you could compile 32bit or 64bit versions. Just another instance where you limit yourself by installing an operating system not specifically created for your hardware.

I know there's a -m32 to be set to gcc, but what variable is used and what do I need to know to do this with a make file? I'd like to compile 32 bit code in 64 bit Linux.

---

### Post by generalguy on 2008-03-29
Well the person you quoted is wrong, ```
-m64
``` should work on any system. Secondly, for makefiles, you'ld need to set the CFLAGS to contain ```
-m32
``` along with any other options.

Try it :

```

#include <stdio.h>

int main()
{
printf("Hello,world! The size of an int pointer is: %z", sizeof(int*));

}

```

See what happens (gcc must be called with argument ```
-std=c99
``` or ```
-std=gnu99
```).

---

### Post by Kilz on 2008-03-29
I have tried it, it may be theoretically possible, but I have never seen it. Not even on simple applications. Say for example [GUatu]("http://guatu.sourceforge.net/").

---

### Post by go_beep_yourself on 2008-03-29
> **generalguy said:**
> Well the person you quoted is wrong, ```
-m64
``` should work on any system. Secondly, for makefiles, you'ld need to set the CFLAGS to contain ```
-m32
``` along with any other options.

Okay, is this right?

```
CFLAGS="$CFLAGS:-m32" ./configure
```

> See what happens (gcc must be called with argument ```
-std=c99
``` or ```
-std=gnu99
```).

Why is that needed and what does it do?

---

### Post by go_beep_yourself on 2008-03-29
> **Kilz said:**
> I have tried it, it may be theoretically possible, but I have never seen it. Not even on simple applications. Say for example [GUatu]("http://guatu.sourceforge.net/").

If that's not the correct way to compile 32 bit code with a 64 bit kernel, then what is?

---

### Post by Kilz on 2008-03-29
> **go_beep_yourself said:**
> If that's not the correct way to compile 32 bit code with a 64 bit kernel, then what is?

You should be able to compile 32bit code on a 64bit system, provided you have the 32bit requirements for the compile. What I wonder is how you would get the 64bit requirements on a 32bit install.

---

### Post by generalguy on 2008-03-30
the -std=c99 forces gcc to use C99, -std=gnu99 forces gcc to use C99 + gnu extensions. You only need that for the example code. 

If you're editing a makefile look for the line that says

CFLAGS = *options*
example:
CFLAGS=-O2 -Wall 

Just append -m32 or -m64 to there.

---

