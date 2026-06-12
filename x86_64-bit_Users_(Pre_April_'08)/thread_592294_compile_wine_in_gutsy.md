---
title: "compile wine in gutsy"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Woody1987 on 2007-10-26
hi, im trying to compile wine 0.9.44 in gutsy 64bit. I'm well aware that there are later versions already available but i need this version to get certain games working, anyway i start off with:

```
CFLAGS="-fno-stack-protector -O2" ./configure --verbose
```

i have tried doing a simple ./configure and i get the same result. I read somewhere that doing the above was necessary on 64bit systems. Regardless, both that code and the simple ./configure produce the same result.

then i do 

```
make depend && make
```

i get

```

{standard input}: Assembler messages:
{standard input}:30: Error: suffix or operands invalid for `push'
{standard input}:31: Error: suffix or operands invalid for `push'
{standard input}:38: Error: suffix or operands invalid for `pop'
{standard input}:39: Error: suffix or operands invalid for `pop'
make[2]: *** [interlocked.o] Error 1
make[2]: Leaving directory `/home/matthew/Desktop/wine-0.9.44/libs/port'
make[1]: *** [port] Error 2
make[1]: Leaving directory `/home/matthew/Desktop/wine-0.9.44/libs'
make: *** [libs] Error 2

```

any ideas?

---

### Post by zorkerz on 2007-10-26
sorry i know little about compiling my strategy is often to search for a deb but 
its an old version of wine and you probably have noticed the link on winehq for 0.9.44 64bit is broken.

---

### Post by Woody1987 on 2007-10-26
i have managed to get a bit further using the instructions on the wine website, but i still get an error during make.

```

/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/matthew/Desktop/wine-0.9.48/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/matthew/Desktop/wine-0.9.48/dlls'
make: *** [dlls] Error 2

```

---

