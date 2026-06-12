---
title: "[SOLVED] error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS6"
date: 2007-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Madj on 2007-12-01
Hi i m totally new with linux and i try to run this program but i ve got a conflict between library. Did somene Know how i can solve this problem?

/usr/apple/shrank/shake4/bin$ tcsh shake
/usr/apple/shrank/shake4/bin/shkx.exe: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64



i ve put the libstdc++5 and the ia32-libs i saw on a forum but it wont change a thing

Also when i make ldd le to find the missing lib it say not a dynamic executable

Can someone,please, explain how i can solved this problem.

---

### Post by Madj on 2007-12-02
Hi no one have any response or advice about where i could get an answer about this problem ?

Hey guys i really some help there ,please.

---

### Post by Kilz on 2007-12-02
> **Madj said:**
> Hi i m totally new with linux and i try to run this program but i ve got a conflict between library. Did somene Know how i can solve this problem?

/usr/apple/shrank/shake4/bin$ tcsh shake
/usr/apple/shrank/shake4/bin/shkx.exe: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64



i ve put the libstdc++5 and the ia32-libs i saw on a forum but it wont change a thing

Also when i make ldd le to find the missing lib it say not a dynamic executable

Can someone,please, explain how i can solved this problem.

Shake is a commercial product. I suggest you contact who you bought it from. There are few posts on this application. [There is only one howto]("http://ubuntuforums.org/showthread.php?t=615277") if those instructions dont help you, and the place you bought it from cant help you. I wish you luck.

---

### Post by Madj on 2007-12-02
> **Kilz said:**
> Shake is a commercial product. I suggest you contact who you bought it from. There are few posts on this application. [There is only one howto]("http://ubuntuforums.org/showthread.php?t=615277") if those instructions dont help you, and the place you bought it from cant help you. I wish you luck.

The problem it  s apple don t know how to manage shake 4.1 wich is a 32 bits application on an other program then fedora and they dont know how to run it on a 64 bits application bu bringing a lib32.

This is a problem wich i can solve with some people who are  able to modify 32bits application for ubuntu 64bits.This is the only way and i m going to make it. ll fight no matter what.

THe problem is close to be solved on this thread [http://ubuntuforums.org/showthread.php?t=629440](http://ubuntuforums.org/showthread.php?t=629440) but i really need some help guys

---

### Post by Cappy on 2007-12-02
32-bit libGL.so.1 is installed from video drivers. I suggest you reinstall whatever drivers you use (ATI, Nvidia, Intel, etc).

ldd isn't working on the file "shake" because it is a scipt that runs an executable; it is not the executable.

For other missing libraries other than libGL.so.1 you can use [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
You can use it, for instance, with libXext.so.6
```
sudo getlibs -32 libXext.so.6
```

Also I should point out libraries in /usr/lib are 64-bit - these are not libraries your 32-bit program can use. It can only use libraries in /usr/lib32 or /lib32. This isn't especially important 

Reading two threads is confusing me.

---

### Post by Madj on 2007-12-02
Thanks Cappy for helping ,i ll try tomorrow and let you know if it s working .

---

### Post by Madj on 2007-12-03
Thank you very much:guitar: it works

---

