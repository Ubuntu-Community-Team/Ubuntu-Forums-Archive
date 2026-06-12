---
title: "quake4 64bit libSDL-1.2.so error - fix"
date: 2007-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by interzoneuk on 2007-06-16
Hi.

I was unable to get quake4 to run in 64bit ubuntu.

I downloaded the ia32 libs and managed to get enemy territory and doom3 to run fine.

However quake 4 threw up this error

./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

I have managed to find a fix though.

I am running the latest stable quake4 -  quake4-linux-1.3-2.x86.run .

- Download this - [http://www.surfels.info/files/q4_amd64.tar.gz](http://www.surfels.info/files/q4_amd64.tar.gz) 
- extract it and copy the files to the quake4 directory (/usr/local/games/quake4)
- run quake4

You should not get the error now.

Hope this helps someone.

---

### Post by jamesford on 2007-06-16
do u know anythin similar for rtcw? it works for me but crashes a lot. worked great in edgy

---

### Post by ucsdrake on 2007-06-24
hey, I have a similar issue when im trying to run the .run for quake 4

```
./setup/sh: 268: /root/.setup9029: not found
./setup/sh: 279: /root/.setup9029: not found
The setup program seems to have failed on x86_64/glibc-2.0

Fatal error, no tech support email configured in this setup
Press Return to close this window...
```

any idea on how to fix this?

---

### Post by Cappy on 2007-06-25
[http://ubuntuforums.org/archive/index.php/t-7616.html](http://ubuntuforums.org/archive/index.php/t-7616.html)

---

### Post by interzoneuk on 2007-08-01
Hi.

I'd just like to say I didn't have to do anything except install all the 32 bit libs - i.e - i did not have to symbolic link anything or extract the executable as mentioned in previous post.

- do a search in adept or what ever package manager you use for 32 and install all libs

here are the main ones

ia32-libs
ia32-libs-sdl
ia32asound2
lib32stdc++6
libc6-i386


And downloaded the archive mentioned in the original post into the q4 dir.

---

