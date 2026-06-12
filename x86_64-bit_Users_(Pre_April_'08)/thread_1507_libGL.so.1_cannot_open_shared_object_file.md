---
title: "libGL.so.1: cannot open shared object file"
date: 2004-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by defcon-1 on 2004-10-21
Every other program I install with apt-get gives me this line when I try to load it,

 ```
error while loading shared libraries&#58; libGL.so.1&#58; cannot open shared object file&#58; No such file or directory
```

It's there darnit! /usr/lib/libGL.so.1 exists!

Any ideas?

---

### Post by dmatrix on 2004-10-21
apt-get install nvidia-glx

---

### Post by defcon-1 on 2004-10-21
It worked, thanks. I didn't try that because I had manualy installed the Nvidia driver, oh well.

---

### Post by spacetree on 2007-01-18
Hi there, i have the same message when trying to use opengl apps.

./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

All my apps tell me the same thing.

Then, when i locate the libGL.so.1, it tells me it exists

spacetree@spacetree-laptop:~/google-earth$ locate libGL.so.1
/home/saul/Backup/libGL.so.1
/home/saul/Backup/libGL.so.1.2
/home/saul/nwn/lib/libGL.so.1
/home/saul/nwn/lib/libGL.so.1.2
/home/saul/nwn/miles/libGL.so.1
/usr/lib/fglrx/libGL.so.1.xlibmesa
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/lib/libGL.so.1.2
/usr/lib/libGL.so.1
/usr/lib32/fglrx/libGL.so.1.xlibmesa
/usr/lib32/fglrx/libGL.so.1.2.xlibmesa
/usr/lib32/libGL.so.1.2
/usr/local/lib/libGL.so.1

Can someone tell me what happens o what should i do?

THX, 

The thing here is that i have installed the fglrx driver (i have ATI) and direct rendering seems to work.

I must say i have a poor framerate (200-400)FPS.

Im using Dapper on a AMD64 Turion X2, with Radeon X1100. Thanks
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5946 (8.27.10)

---

### Post by onlinecode on 2007-02-14
use root run it ok... 
(&#29992;root&#36523;&#20221;&#36816;&#34892;&#23601;&#21487;&#20197;&#20102;)

---

### Post by prince_niceguy on 2007-02-14
do a chmod 755 for the files to be readable anyone...

---

### Post by RAOF on 2007-02-15
Your problem is that Google Earth is a 32bit program, so needs a 32bit libGL.  The nvidia-glx package has a 32bit libGL in it, but I'm not sure about the fglrx drivers.  It's possible that they just suck.

Alternatively, run "sudo ln -s /usr/lib32/libGL.so.1.2 /usr/lib32/libGL.so.1"

---

### Post by prince_niceguy on 2007-02-15
i am using ati and i followed this thread or something of similar in google community... now it works like a charm... :)

[http://bbs.keyhole.com/ubb/showflat.php?Cat=0&Board=SupportGELinux&Number=620003&page=2&fpart=2](http://bbs.keyhole.com/ubb/showflat.php?Cat=0&Board=SupportGELinux&Number=620003&page=2&fpart=2)

---

