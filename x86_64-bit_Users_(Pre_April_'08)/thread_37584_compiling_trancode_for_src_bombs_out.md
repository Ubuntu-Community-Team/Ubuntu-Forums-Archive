---
title: "compiling trancode for src bombs out"
date: 2005-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by KRavEN on 2005-05-27
apt-get -b source transcode

Had to get a ton of dependencies.  When I finally got them all it bombs out here:

```
x86_64-linux-gcc -shared  .libs/import_ffmpeg.o  -L/usr/lib64 -lavcodec -lm -lz -ldl  -Wl,-soname -Wl,import_ffmpeg.so -o .libs/import_ffmpeg.so
/usr/bin/ld: /usr/lib64/libavcodec.a(utils.o): relocation R_X86_64_32S can not be used when making a shared object; recompile with -fPIC
/usr/lib64/libavcodec.a: could not read symbols: Bad value
```

---

### Post by estel on 2005-06-07
Yeh, i've just got exactly the same problem (this is trying to compile transcode in order to get DVD rip to work). There's only libavcodec-dev in the repository; where's libavcodec?

---

### Post by Drain on 2005-06-07
Just curious, did you do the 

$ apt-get build-dep transcode 

step before trying to build from source (I can't count the number of times I've forgotten a dependency before trying to build something from source ;-) )

---

### Post by X3N on 2005-06-08
Linux Fornax 2.6.10-5-amd64-k8 #1 Tue Jun 7 08:26:38 UTC 2005 x86_64 GNU/Linux

I have transcode working 
transcode-0.6.14

I compiled it myself, you do need to install a lot of dev packages to get it working.

---

### Post by KRavEN on 2005-06-09
I had to have all the dependencies fulfilled before apt-get --build source transcode would proceed to start building the package.

---

### Post by KRavEN on 2005-06-09
[QUOTE=X3N]Linux Fornax 2.6.10-5-amd64-k8 #1 Tue Jun 7 08:26:38 UTC 2005 x86_64 GNU/Linux

I have transcode working 
transcode-0.6.14

I compiled it myself, you do need to install a lot of dev packages to get it working.[/QUOTE]

Did you compile it from the tar source from transcode or did you compile it from one of the repository debian sources?  If you did so from the debian sources maybe you could post your resulting deb file so the rest of us can get on the transcode wagon too.    :-)

---

### Post by X3N on 2005-06-12
I downloaded the source tar.gz from [http://www.transcoding.org/](http://www.transcoding.org/)  and gradually resolved the dependencies.

---

### Post by hva on 2005-06-13
i succeded as well, but had to recompile ffmpeg with shared library before.

---

