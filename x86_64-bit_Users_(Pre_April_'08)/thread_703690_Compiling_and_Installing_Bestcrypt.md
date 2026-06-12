---
title: "Compiling and Installing Bestcrypt"
date: 2008-02-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by C. Wizard on 2008-02-21
Has anyone had any success in compiling and installing Bestcrypt on 7.10 amd64?
I've tried and get this error message:

:/tmp/bcrypt-1.6-13$ sudo make
set -e; for i in kgsha kgsha256 src mod; do make -C $i CC=gcc CPP=g++ ; done
make[1]: Entering directory `/tmp/bcrypt-1.6-13/kgsha'
g++ -fPIC -Wall -fno-strength-reduce -I../include -O2  -c -o alg.o alg.cpp
make[1]: g++: Command not found
make[1]: *** [alg.o] Error 127
make[1]: Leaving directory `/tmp/bcrypt-1.6-13/kgsha'
make: *** [subdirs] Error 2"

g++ is installed.
Any ideas greatly appreciated.
Thank you.

---

