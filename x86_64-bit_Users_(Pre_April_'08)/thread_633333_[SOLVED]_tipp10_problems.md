---
title: "[SOLVED] tipp10 problems"
date: 2007-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by soxs on 2007-12-06
tipp10 is a german tipptrainer. It has a really neat serface/gui and i like it a lot.
It's a standalone executable which runs fine under 32 bit gutsy gibbon

But now under 64bit gutsy I get this error when starting in console
```
$ ./tipp10
./tipp10: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory

```

I allready made sure that I've installed the named library. The forum @ tipp10.de wasn't able to help me :-( plx help

---

### Post by Cappy on 2007-12-06
```
sudo apt-get install libpng3
```
doesn't fix the problem?

Because the libpng3 library says it is for all architectures you should try
```
sudo cp /usr/lib/libpng.so.3 /usr/lib32/libpng.so.3
sudo ldconfig

```

Posting ```
ldd tipp10
``` may help.

---

### Post by soxs on 2007-12-07
ok... here we go:
I've done all suggested steps and now I get a different error *g*:
```
# ./tipp10
./tipp10: error while loading shared libraries: libpng.so.3: wrong ELF class: ELFCLASS64

```

```
# ldd tipp10
        linux-gate.so.1 =>  (0xffffe000)
        libpng.so.3 => not found
        libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7f55000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0xf7f3d000)
        libXi.so.6 => /usr/lib32/libXi.so.6 (0xf7f35000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7f2d000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf7f27000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf7f22000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf7f19000)
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7f15000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf7ea5000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf7e7a000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7e6c000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7d7b000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7d66000)
        libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf7d60000)
        libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf7ca3000)
        librt.so.1 => /lib32/librt.so.1 (0xf7c9a000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7c96000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7c7e000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7b8b000)
        libm.so.6 => /lib32/libm.so.6 (0xf7b65000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7b5a000)
        libc.so.6 => /lib32/libc.so.6 (0xf7a10000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf79f0000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf79ed000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf79e7000)
        /lib/ld-linux.so.2 (0xf7f74000)

```

ideas?

---

### Post by Cappy on 2007-12-07
Well, that helps; It tells me the packages.ubuntu page is wrong for some reason. Here is the solution:

Install getlibs here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and now change to the directory of tipp10 and run
```
sudo getlibs tipp10
```
or alternatively,
```
sudo getlibs -32 libpng.so.3
```

---

### Post by soxs on 2007-12-08
*thumbs up*
Your program is.. Boah! I love it! Workx like charm!

I used ```
sudo getlibs tipp10
``` and it worked.

Thx very much!

---

