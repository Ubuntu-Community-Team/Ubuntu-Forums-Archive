---
title: "Problem Compiling Wine from Source"
date: 2008-05-16
forum: Wine
---

### Post by Mausamber on 2008-05-16
I am running Hardy Heron, and have been trying to compile Wine 0.9.57 from source. I have tried various times and it keeps giving me:

/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/avi/wine-0.9.57/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/avi/wine-0.9.57/dlls'
make: *** [dlls] Error 2

could anyone tell me what the error is saying, and what I should do to fix it.

---

### Post by cogadh on 2008-05-17
Are you trying to compile on a 64bit system? If so, just follow the instructions here:
[http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873](http://wiki.winehq.org/WineOn64bit#head-7703cf4cc6b63630523cf66e77d621e4f81bc873)

On a side note, is there a particular reason you need to compile an out of date Wine version? Generally speaking, it is usually better to use the latest version, except if that version contains a regression that affects a particular app you are trying to run.

---

### Post by YokoZar on 2008-05-17
If you just want to use 0.9.57, rather than compiling it yourself you could just install the Gutsy .debs here: [http://wine.budgetdedicated.com/archive/](http://wine.budgetdedicated.com/archive/)

---

### Post by Mausamber on 2008-05-17
I'm trying to compile the old version due to a regression in World in Conflict, plus I wanna add the battlenet patch for warcraft 3 and alphablend patch for CoD4. Also, I'm trying to later make seperate versions of wine all at the same time for running seperate things.

Thank You very much for your quick replies.

---

### Post by Mausamber on 2008-05-17
I tried using the instructions from the website and now it gives me this error:

/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc-4.2 failed
make[2]: *** [winex11.drv.so] Error 2
make[2]: Leaving directory `/home/avi/wine-0.9.57/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/avi/wine-0.9.57/dlls'
make: *** [dlls] Error 2

this looks like almost the same thing. I'm compiling it with no patches or anything, so I'm not sure why its doing this. I followed the instructions on the winewiki to the dot. IF this doesn't work could someone make deb with the wine 0.9.57 and the cod4 and battlenet patch please.

---

### Post by Mausamber on 2008-05-17
Nvm, I have managed to compile it now, it was my fault as I had misunderstood one of the instructions.

Once again, thank you for all your help.

---

