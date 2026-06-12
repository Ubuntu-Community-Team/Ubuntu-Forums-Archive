---
title: "libstdc++2.10-glibc2.2 missing"
date: 2006-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by BigCdaAnswer3 on 2006-03-16
I am trying to run a program which spits this out:

error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

I have googled EXTENSIVELY only to come up with a package (libstdc++2.10-glibc2.2) which i cannot find anywhere for amd64....i can find it for i386 though!! anybody know of how/where to get this.....

---

### Post by Koobi on 2006-03-16
i very vaguely remember this being one of the dependencies of acroread but i'm not sure.
maybe installing acroread via apt/aptitude will fix this for you?

---

### Post by BigCdaAnswer3 on 2006-03-16
Already found a solution to my problem. I was trying to run a 32-bit executable which i thought was a 64-bit....after doing some experimenting i ended up installing the i386 version with a:

dpkg -i --force-architecture libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

and then symlinking:

ln -s /usr/lib/libstdc++-libc6.2-2.so.3 /usr/lib/libstdc++libc6.1-1.so.2

and it works! yay for me. issue resolved. hope this can help some other people too. 

If anyone is wondering what I was trying to run it was one of the standalone apps from blender.org -- 

[http://blender3d.org/cms/Stand-alones.162.0.html](http://blender3d.org/cms/Stand-alones.162.0.html)

---

### Post by ridvan on 2006-05-08
I have used these instructions to install and run Java Studio Creator 2 update 1 on a X2 4400 with Dapper Drake flight 7 amd64

---

