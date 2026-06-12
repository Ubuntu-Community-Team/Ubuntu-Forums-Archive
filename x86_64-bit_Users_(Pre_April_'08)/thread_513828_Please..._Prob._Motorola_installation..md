---
title: "Please... Prob. Motorola installation."
date: 2007-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by ahchong on 2007-07-30
i just bought my V3X. then i try to flash it with LInux. i found some steps ut it went wrong in some way. 
ive encounter problem.. it wont install moto4lin after following this site. 

[http://ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin](http://ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin)

it wrote:

root@Emily:~/moto4lin# make install
( [ -d moto_ui ] && cd moto_ui ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d moto_ui ] && cd moto_ui ; make -f Makefile install; ) || true
make[1]: Entering directory `/home/ahchong/moto4lin/moto_ui'
g++ -c -pipe -Wall -W -g -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -Iui/ -I. -Imoc/ -o obj/main.o main.cpp
make[1]: g++: Command not found
make[1]: *** [obj/main.o] Error 127
make[1]: Leaving directory `/home/ahchong/moto4lin/moto_ui'




what i should do first? 
or give me the better way of solution.

---

### Post by PaulFr on 2007-07-31
Please run ```
sudo apt-get install build-essential
``` to install the gcc and g++ compilers.

---

### Post by ahchong on 2007-07-31
hehehe... thanks bro for the method.
actually i found the way just this morning during my medical class..
hehehe... cause the how-to-install for the motorola not yet understandable.

does moto4lin has autostart? without type in the terminal?

---

