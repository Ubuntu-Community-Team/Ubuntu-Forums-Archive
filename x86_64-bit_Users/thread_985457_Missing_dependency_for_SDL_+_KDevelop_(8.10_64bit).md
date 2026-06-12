---
title: "Missing dependency for SDL + KDevelop (8.10 64bit)"
date: 2008-11-17
forum: x86 64-bit Users
---

### Post by gweedo767 on 2008-11-17
I am just trying to build a sample SDL app in KDevelop and getting:
../libtool: line 2141: X-R/usr/lib: No such file or directory

I can't figure out which dependency I am missing...

---

### Post by cariboo on 2008-11-17
Have you got the libtool package installed. When searching for missing dependencies I find using the search button in Synaptic helpful as you can search by name and description.

Jim

---

### Post by Yellow Pasque on 2008-11-18
Just to check the obvious: Do you have the SDL -dev package(s) installed?
```
sudo apt-get install libsdl1.2-dev
```

---

### Post by Black Serpent on 2009-02-09
I have exactly the same problem.

BTW - I have managed to fully compile under CodeBlocks a sample SDL.

---

### Post by zilitor on 2009-03-06
I'm having the exact same problem. 

"I am just trying to build a sample SDL app in KDevelop and getting:
../libtool: line 2141: X-R/usr/lib: No such file or directory"

I have both libtool and libsdl packages installed. Any help is appreciated.

---

### Post by wonko on 2009-10-06
Sorry for bringing up an old thread, but I too encountered this problem recently (running kubuntu 9.04 64bit). I found the fix on a polish forum ([http://forum.pclab.pl/t512306.html](http://forum.pclab.pl/t512306.html) - don't know polish, but at the bottom there's an English citation).

So the solution: Just copy /usr/share/libtool/config/ltmain.sh to your project folder (overwriting the existing one).

If anyone know a permanent fix, or why this occurs in the first place, a comment is greatly appreciated (either by pm or to this thread).

Hope this can be of help to someone...

---

