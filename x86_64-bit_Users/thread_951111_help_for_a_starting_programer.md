---
title: "help for a starting programer"
date: 2008-10-17
forum: x86 64-bit Users
---

### Post by blackmail on 2008-10-17
ok, i think i have to start at the begining...
i moved to ubuntu for a month now, and today i installed the 64bit LTS version of hardy...and had a sudden apetite for starting C.
but i ran into some problems like, even a simple file llike

#include <stdio.h>
main()
{
 printf("how old are you");
 int age;
 scanf("%d", &age);
 printf("...so your age is %d", age);
 return 0;
}

when i run it with gcc it gives interesting messages like...

blackmail@Diaryofamadman:~/c_sources$ gcc test.c
test.c:1:19: error: stdio.h: No such file or directory
test.c: In function &#8216;main&#8217;:
test.c:4: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
test.c:6: warning: incompatible implicit declaration of built-in function &#8216;scanf&#8217;

am i doing something wrong here...?
I mean i do this in windows and it works dandy...

if it helps my system is amd64 4600 x2, 1gb ram, 160gb WD hard drive, gygabite socket am2 mainboard, with sound, video integrated

---

### Post by blackmail on 2008-10-17
ok i solved my issue, it was a simple line sudo apt-get install build-essential
...but any suggestions are welcome for a nice compiler with GUI

---

### Post by soxs on 2008-10-17
Compilers don't have GUIs, or they are limited in options.

There are books about compiler options and stuff...

---

### Post by jespdj on 2008-10-18
Look around in the [Programming Talk forum](http://ubuntuforums.org/forumdisplay.php?f=39). What you're looking for is an IDE (Integrated Development Environment).

There are several IDE's available for Linux, for example Code::Blocks, Anjuta, Kdevelop (for the KDE desktop), Eclipse and NetBeans (both of those are mainly aimed at Java but can also be used for C/C++).

---

### Post by tenghoward on 2008-10-20
If you are looking for IDE, I recommand Code::Blocks. In my opinion it is more user friendly.

---

### Post by blackmail on 2008-10-21
:popcorn:
yes the code::blocks solved my issue
thnx all

---

