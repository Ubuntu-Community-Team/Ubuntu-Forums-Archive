---
title: "Best suited Linux"
date: 2008-12-24
forum: x86 64-bit Users
---

### Post by kristian_k on 2008-12-24
Hi all,
I have the following configuration:

[I][COLOR="DarkOrange"]Athlon64 X2 TK-57
4GB RAM
250GB hard disk
ATI X1250[/COLOR][/I]

I have trouble finding an OS that works for me, it needs to be 64bit since I have 4GB of RAM, also it should be well equipped for programming in C, C++, JAVA, PHP etc...
I tried Fedora 10 - crashed allot 
also Ubuntu 8.10 has an issue with the CPU - I get very slow performance because CPU usage is over 90%, sometimes 100% and no apps are running. 
So if anyone can suggest a Linux OS that would work for my need, 
than you!

---

### Post by hyperdude111 on 2008-12-24
You could try th 32 bit ubuntu and them install the kernel for the server edition. This allows you to use 32 bit and all of your ram.

---

### Post by kristian_k on 2008-12-24
> **hyperdude111 said:**
> You could try th 32 bit ubuntu and them install the kernel for the server edition. This allows you to use 32 bit and all of your ram.

I am sort of .. well.. not an expert at Linux so if you could direct me to a tutorial on how to do install the kernel for server edition that would be great!  :)

---

### Post by redsoxreed on 2008-12-24
You could try Debian.

---

### Post by hyperdude111 on 2008-12-24
I believe these are the commands for more than 3.5 GB of Ram on 32bit.

" sudo apt-get install linux-restricted-modules-server "
" sudo apt-get install linux-headers-server "
" sudo apt-get install linux-image-server linux-server "

I know this works for 8.04 and it should work on 8.10 although i have not tested it. Good Luck and Merry Xmas

~Hyper~

---

### Post by obsrv on 2008-12-25
My recommendations:
[LIST=1]
[*]Baltix GNU/Linux
[*]Debian GNU/Linux
[*]Ubuntu/KUbuntu
[/LIST]

---

### Post by halovivek on 2008-12-25
install ubuntu 32 bit. it will work good. i have done that for one computer

---

### Post by obsrv on 2008-12-25
> **halovivek said:**
> install ubuntu 32 bit. it will work good. i have done that for one computer

If you offer ubuntu I recommend for both of you try Baltix GNU/Linux. It is the same Ubuntu, just with preinstalled codecs. Everything just works out of the box. But this distro is illegal in USA. Sorry :)

---

### Post by Sef on 2008-12-25
> If you offer ubuntu I recommend for both of you try Baltix GNU/Linux. It is the same Ubuntu, just with preinstalled codecs. Everything just works out of the box. But this distro is illegal in USA. Sorry :smile:

To install codecs in Ubuntu is very easy nowadays.  Also I would try the 64-bit Ubuntu since your system is 64-bit.

---

### Post by steveneddy on 2008-12-27
> **Sef said:**
> To install codecs in Ubuntu is very easy nowadays.  Also I would try the 64-bit Ubuntu since your system is 64-bit.

I agree. 64 bit Ubuntu is truly the way to go.

Codecs aren't really a problem anymore. Media plays fine on my 64 bit laptop.

Maybe you could locate a local Linux Users Group (LUG) to help you install your new OS and help you understand operating systems and your new Linux OS in particular a little better.

I use Ubuntu 8.04 64 bit due to stability and Long Term Support.

Good luck.

---

### Post by jespdj on 2008-12-27
> **kristian_k said:**
> I tried Fedora 10 - crashed allot 
also Ubuntu 8.10 has an issue with the CPU - I get very slow performance because CPU usage is over 90%, sometimes 100% and no apps are running. 
So if anyone can suggest a Linux OS that would work for my need, 
than you!
Instead of trying another Linux distribution (or going to 32-bit...), try finding out what the problem actually is.

For example, to find out what's eating up your CPU while you aren't running any programs, run:
```
top
```
in a terminal window to find out which process is using the CPU. Tell us what it is and we can help you solve the problem.

It's not normal that 64-bit Ubuntu eats up all your CPU when you're not doing anything on the computer.

64-bit Ubuntu is very well suited fo developing in C, C++, Java, PHP etc.

---

