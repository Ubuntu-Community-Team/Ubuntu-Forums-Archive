---
title: "gcc compiler problem"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by rediculable on 2008-04-27
Hey, I'm new here so go easy on me.  I just installed the 8.04 64bit version.  I thought I'd test out the compiler.  I wrote up a simple "Hello World" program in C and tried compiling it with the usual:
gcc hello.c -o hello

I got several error messages.  stdio.h was not recognized.  It didn't recognize "main", and of course "printf" wasn't recognized either as it couldn't find the header.

I'm new to programming, Ubuntu, and computers in general, but it seems to me like the compiler is present, but the libraries are not.  But I dunno.  Maybe hicks and computers don't mix.

---

### Post by vambo on 2008-04-27
I think you need the build-essential package

```
sudo apt-get install build-essential
```

---

### Post by rediculable on 2008-04-27
Yup, that did, thank you.  I don't understand why the compiler is present, but not the needed dependencies.  Can anyone enlighten me.  Is it simply for a simpler installation?

---

### Post by vambo on 2008-04-27
That is a very good question. One to which I have no answer !!!

---

### Post by RAOF on 2008-04-27
The key package that build-essential installed was *libc6-dev*, which contains the standard C library headers and such.  The reason this isn't installed by default when you install gcc is that it's quite possible to use gcc without the standard library (for example, kernel compilation does not require the std library).

---

### Post by captain_hideous on 2008-05-10
I have a similar problem. gcc will not compile simple hello_world.c program. I have tried installing libc-dev and build-essential
this is what I get
------------------------------------
main.c:1:19: warning: extra tokens at end of #include directive
main.c:1:20: error: no include path in which to search for stdio.h
main.c: In function 'main':
main.c:5: error: 'printf' undeclared (first use in this function)
main.c:5: error: expected ';' before string constant
e path in which to search for stdio.h
-----------------------------------------

---

### Post by RAOF on 2008-05-11
I think your problem is in your code; could you post it?

---

### Post by negora on 2008-05-12
Well, I know that it isn't a thread to opine about this, but I also think that installing "build-essential" by default would be very helpfull, specially for those who need to compile something just after the installation (such as a WiFi adapter driver), have no idea about programming, can't reach the Internet, and just follow the instructions which the manufacturer includes in the classic README.

---

### Post by sandy06 on 2009-04-28
I am getting E:couldn't find packet build-essential
so what to do...
please help me out..

i did #sudo apt-get install build-essential

---

### Post by userp on 2009-04-28
hi every one

[B]hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function &#8216;main&#8217;:
hello.c:6: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;[/B]


i am get this error when  i am  compiling hello.c

#include<stdio.h>
void main()
{
printf("Hello world");

}

i hav tried [B]sudo apt-get install build-essential
[/B]and sucessfully installed 
but i am still getting this error
plz help

---

### Post by ethoxyethaan on 2009-04-29
> **userp said:**
> hi every one

[B]hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:6: warning: incompatible implicit declaration of built-in function ‘printf’[/B]


i am get this error when  i am  compiling hello.c

#include<stdio.h>
void main()
{
printf("Hello world");

}

i hav tried [B]sudo apt-get install build-essential
[/B]and sucessfully installed 
but i am still getting this error
plz help

works for me,

try installing libc6-dev

---

### Post by stchman on 2009-04-29
It is ridiculous that the build-essential package is not installed by default in Ubuntu.  There are times that a user needs to make a driver so a fully functioning C compiler is needed.

---

### Post by jespdj on 2009-04-29
> **stchman said:**
> It is ridiculous that the build-essential package is not installed by default in Ubuntu.  There are times that a user needs to make a driver so a fully functioning C compiler is needed.
To build drivers, you often do not need the full libc6-dev. Note that drivers that run in kernel mode cannot use the standard C library functions anyway (they have to use the kernel functions instead).

To build for example the nVidia kernel module you don't need build-essential; you can do that with the gcc that is installed by default.

---

### Post by stchman on 2009-04-30
> **jespdj said:**
> To build drivers, you often do not need the full libc6-dev. Note that drivers that run in kernel mode cannot use the standard C library functions anyway (they have to use the kernel functions instead).

To build for example the nVidia kernel module you don't need build-essential; you can do that with the gcc that is installed by default.

Not often, but maybe.  I am just amazed that they do not include that package.

---

