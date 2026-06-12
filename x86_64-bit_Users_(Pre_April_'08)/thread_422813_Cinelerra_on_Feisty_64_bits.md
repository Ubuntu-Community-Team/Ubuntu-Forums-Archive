---
title: "Cinelerra on Feisty 64 bits"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by DanielG007 on 2007-04-25
Hello, I have a problem with compiling cinelerra, i have downloaded the source code of cvs.cinelerra.org but i can't compile it, I use Feisty 64bits.

me -Wl,libquicktimehv-1.6.0.so.1 -o .libs/libquicktimehv-1.6.0.so.1.0.0
/usr/bin/ld: ffmpeg/libavcodec/.libs/libavcodec.a(mpegvideo_mmx.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
ffmpeg/libavcodec/.libs/libavcodec.a(mpegvideo_mmx.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libquicktimehv.la] Error 1
make[3]: se sale del directorio `/home/dani/pandodl-16837/hvirtual/quicktime'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/home/dani/pandodl-16837/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/dani/pandodl-16837/hvirtual'
make: *** [all] Error 2
root@amd64:/home/dani/pandodl/hvirtual# 


Any solution?

---

### Post by kuja on 2007-04-29
What's the status on this for you? I tried to compile cinelerra back when I was running edgy and it was  like a dependancy nightmare ...

---

### Post by jkwarras on 2007-04-30
You could try this repositories:

## Lprod repository
deb [http://lprod.org/deb/dapper/](http://lprod.org/deb/dapper/) ./
# deb-src [http://lprod.org/deb/dapper/](http://lprod.org/deb/dapper/) ./

## Cinelerra ubuntu edgy amd64
deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./
# deb-src [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./

Both have 64 bits Cinelerra packages.

---

