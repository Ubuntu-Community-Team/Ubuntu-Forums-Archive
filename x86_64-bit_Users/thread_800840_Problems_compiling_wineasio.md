---
title: "Problems compiling wineasio"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by etherior on 2008-05-20
Hello I'm trying to compile wineasio 0.7.3 on my UbuntuStudio 8.04 (obviously 64bit) , but when I launch make receive the following output:

winegcc -shared wineasio.dll.spec -mnocygwin -o wineasio.dll.so asio.o main.o regsvr.o     -ljack  -lodbc32 -lole32 -loleaut32 -lwinspool -lwinmm -lpthread -luuid
/usr/bin/ld: skipping incompatible /usr/lib/libjack.so when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/libjack.a when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libjack.so when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libjack.a when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libjack.so when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libjack.a when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/libjack.so when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/libjack.a when searching for -ljack
/usr/bin/ld: cannot find -ljack
collect2: ld returned 1 exit status
winegcc: gcc failed

I've installed libjack-dev, so is there a way to solve the problem?

---

### Post by richie.mort on 2008-05-28
Any progress with this? I get a similar error trying to make the wineasio:

winegcc -shared wineasio.dll.spec -mnocygwin -o wineasio.dll.so asio.o main.o regsvr.o     -ljack  -lodbc32 -lole32 -loleaut32 -lwinspool -lwinmm -lpthread -luuid
/usr/bin/ld: skipping incompatible /usr/lib/libjack.so when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/libjack.a when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libjack.so when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libjack.a when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libjack.so when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libjack.a when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/libjack.so when searching for -ljack
/usr/bin/ld: skipping incompatible /usr/lib/libjack.a when searching for -ljack
/usr/bin/ld: cannot find -ljack
collect2: ld returned 1 exit status
winegcc: gcc failed
make: *** [wineasio.dll.so] Error 2

---

