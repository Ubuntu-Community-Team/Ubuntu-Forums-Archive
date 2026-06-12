---
title: "Compiling C++ program for i386 architecture"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by Stargazer712 on 2008-05-02
Ok, I am trying to compile a very simple c++ program using g++. The computer that I am compiling it on is using an x86_64 architecture, and the computer it will be run on is using an i386 architecture.

I need to be able to compile the program on my computer (x86_64) and run it on the i386 computer. Are there any options on g++ that will allow me to compile for a different architecture?

thanks in advance.

---

### Post by Grishka on 2008-05-02
I believe it needs the "-m32" option. also, you'll probably need 32-bit libraries for that.

---

### Post by vishalrao on 2008-05-03
see if installing packages like ia32-libs, linux32 and gcc-multilib helps.
do "aptitude search lib32" for more stuff you might want.

i have done it and needed to include "/usr/lib32" in a conf file in /etc/ld.so.conf.d/ and also made a symlink "ln -s /usr/lib32/libstdc++.so.6.0.9 /usr/lib32/libstdc++.so"  - you can point to the .5 version if you need...

HTH

---

