---
title: "Hardy-64 Compiling Sauerbraten"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by javagamer on 2008-05-02
Hi,
   I've scoured the net and I can't seem to find a way to get Sauerbraten to compile on Hardy64, I got Sauerbraten from CVS and cd'ed to src, but once I type make I get an error:
```
g++ -Wall -fsigned-char -O3 -fomit-frame-pointer -Ishared -Iengine -Ifpsgame -Irpggame -Ienet/include -I/usr/X11R6/include `sdl-config --cflags`   -c -o shared/tools.o shared/tools.cpp
shared/tools.cpp: In function ‘char* makerelpath(const char*, const char*, const char*)’:
shared/tools.cpp:29: error: no matching function for call to ‘min(int, long int)’
make: *** [shared/tools.o] Error 1
```
Can anyone help?  I'm rather new to Ubuntu so I might be missing something obvious.

---

### Post by ZeroHimself on 2008-05-02
I just ran the version in the repos

```
sudo apt-get install sauerbraten
```

;-)

worked for me...

---

### Post by PC_load_letter on 2008-05-03
I am still on Feisty 64bit and I'm running SauerBraten with no problems. I followed the guide on this page: [http://gaming.gwos.org/doku.php/games:alphabetical:c:cube](http://gaming.gwos.org/doku.php/games:alphabetical:c:cube)

There is also a .deb package from GetDeb, but I'd try to compile it first. 
Great game by the way, would love more AI.

---

### Post by javagamer on 2008-05-03
Thanks for the help, I discovered what is wrong.  I wanted the newest version from the CVS, but for some reason that won't compile on Hardy-64 (not sure about any other OS), so I got an older version and it compiles fine.

---

### Post by Perfect Storm on 2008-05-03
That's CVS and SVN is for, breaking stuff, testing for the developers ;)
Good idea to search their forum for the error if it's not there, report it.

---

### Post by Butthead on 2008-05-03
[QUOTE=PC_load_letter;4868990Great game by the way, would love more AI.[/QUOTE]

I'd settle for a bit more ammo (and running into less of those dang Baal's so early in the SP levels) myself. 8-[

---

