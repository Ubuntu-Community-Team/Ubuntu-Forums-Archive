---
title: "Cannot re-compile from source code"
date: 2006-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by sayantan on 2006-01-09
Hi 

I've installed the ubuntu x86_64 (AMD64) , and everything seems to be working fine, except for a few things.. 

I cannot re-compile some packages from the source codes, for example i cannot install xmms, the vanila kernel (2.6.x) , and some other x apps ... 

The xmms fails in ./configure saying that the installation is missing zlib, but when I checked aptitude, I found the zlib package already installed. 

The same with the libraries of other x apps ... The installation has the required libraries installed (libx11, libxmu, libxt.. etc), but cannot compile them.. fails in the ./configure stage.

What are the compiler options for compiling lets say a simple X application, in an Ubuntu.

Any ideas? 

Please help.

---

### Post by t3r0 on 2006-01-11
You need to install also the dev packages of the needed libs... for example if configure scripts says your system is missing zlib, try installing zlib-dev package..


- Tero

---

