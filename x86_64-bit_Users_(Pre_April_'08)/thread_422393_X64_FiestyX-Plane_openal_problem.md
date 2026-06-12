---
title: "X64_Fiesty/X-Plane openal problem"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by womail on 2007-04-25
Hi,

I am running fiesty fawn X64 and I am trying to run X-Plane. The X-Pane
executable fails because it cant find libopenal.so.0. This library is
installed in /usr/lib but /usr/lib32 does not contain libopenal.so.0.

I tried link the /usr/lib/libopenal.so.0 to /usr/lib32/libopenal.so.0, no good

I got an i386 version of the .deb but I cannot install it because it is
not suitable for my system. 

I tried alien to convert a suse 9.2 openal-32bit, but it did not work either.

I suspect I need a 32bit compatible libopenal.so.0, but I can't make adept only give me 32 bit version either.

Agghhhh...

Has anyone managed to solve this problem ??

Thanks

---

### Post by darrenh on 2007-05-23
Just bought X-plane and have exactly the same problem.

I found this post regarding downloading the 32 bit version, extracting it and putting it in /usr/lib32 

[http://ubuntuforums.org/archive/index.php/t-135337.html](http://ubuntuforums.org/archive/index.php/t-135337.html)

but that didn't work for me.

I've e-mailed x-plane. They've responded, but no solution yet.

---

### Post by darrenh on 2007-05-23
ok, got the installer running now

Download the 32-bit version of libopenal

This is libopenal0a_0.0.8-3_i386.deb at time of posting

Extract the files in the current directory using

dpkg-deb -x libopenal0a_0.0.8-3_i386.deb .

Copy libopenal.so.0.0.0 from the lib directory created above to /lib32  (not /usr/lib32)

Create a symlink

ln -s /lib32/libopenal.so.0.0.0 lib32/libopenal.so.0

I'm now running the DVD installer from the web. 


another post for you to look at 

[http://www.xplanefreeware.net/forums/index.php?showtopic=677&hl=linux+install+openal](http://www.xplanefreeware.net/forums/index.php?showtopic=677&hl=linux+install+openal)

---

