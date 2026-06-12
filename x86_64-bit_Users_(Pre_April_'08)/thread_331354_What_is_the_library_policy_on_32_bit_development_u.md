---
title: "What is the library policy on 32 bit development under a x86_64 ?"
date: 2007-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by rockets on 2007-01-04
This is my issue. I do some 32 bit development on Edgy x86_64. For this to work, I had to cerate some links in /usr/lib32 (see bug #77987). 

I've had to also compile, and install, 32 bits versions of tools like freeglut and fftw3 with their development headers. I installed them in /usr/local/lib32, added that path to my /etc/ld.so.conf and ran ldconfig. Everything is fine now.
In Edgy, it appears that every 32 bit library is intended to be at /usr/lib32, but I desisted from putting them there for version tracking reasons and because others things are installed apart from just the .so files.

So the question is: in an x86_64 are we supposed to have 32 bit development versions of all
libraries at /usr/lib32 ?

Another question: I cannot force install a 32 bit .deb package because it will go into the /lib and that is intende for 64 bit libraries in x86-64. Am I right ?

---

