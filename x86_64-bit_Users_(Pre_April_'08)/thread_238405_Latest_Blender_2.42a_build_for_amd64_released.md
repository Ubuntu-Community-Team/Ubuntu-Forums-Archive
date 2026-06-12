---
title: "Latest Blender 2.42a build for amd64 released"
date: 2006-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2006-08-17
haven't checked it out yet but looks like native amd64 builds of blender are available below, how cool is that?

[http://www.blendernation.com/2006/07/26/optimized-blender-242a-for-windows-and-linux/](http://www.blendernation.com/2006/07/26/optimized-blender-242a-for-windows-and-linux/)

---

### Post by Ahriman on 2006-08-18
Have you managed to get it to work yet? I installed Ubuntu 64-bit last night, and tried installing the Optimised build this morning, and it keeps giving me an error about libpython2.4.so.1.0 not found, even though it's in /usr/lib.
(although this is probably due to me not having set up Ubuntu64 correctly)

I installed the optimised build on 32-bit Ubuntu and it is a damn site quicker. Lets hope they keep it up :)

---

### Post by jonah1980 on 2006-08-18
yeah your right dude. i got the same error!

---

### Post by KhaaL on 2006-09-05
is there any 64bit libpython2.4 package yet?

---

### Post by Kilz on 2006-09-05
> **Khalid Rashid said:**
> is there any 64bit libpython2.4 package yet?

[http://packages.ubuntu.com/dapper/python/python2.4](http://packages.ubuntu.com/dapper/python/python2.4)

---

### Post by KhaaL on 2006-09-05
> **Kilz said:**
> [http://packages.ubuntu.com/dapper/python/python2.4](http://packages.ubuntu.com/dapper/python/python2.4)

Thanks a bunch!

it's weird, but even with that package installed, running blender results in:

"blender-bin: error while loading shared libraries: libpython2.4.so.1.0: cannot open shared object file: No such file or directory"

I grabbed a optimized build at 

[http://ruicampos.com/fl_tmp/debian/ubuntu-dapper/2.42a/athlon64/](http://ruicampos.com/fl_tmp/debian/ubuntu-dapper/2.42a/athlon64/)

and it does not give any  dependency complaints  :-k

---

### Post by jonah1980 on 2006-09-05
awesome i'll try the build you found instead, thanks for the link

---

### Post by Kilz on 2006-09-05
> **Khalid Rashid said:**
> Thanks a bunch!

it's weird, but even with that package installed, running blender results in:

"blender-bin: error while loading shared libraries: libpython2.4.so.1.0: cannot open shared object file: No such file or directory"

I grabbed a optimized build at 

[http://ruicampos.com/fl_tmp/debian/ubuntu-dapper/2.42a/athlon64/](http://ruicampos.com/fl_tmp/debian/ubuntu-dapper/2.42a/athlon64/)

and it does not give any  dependency complaints  :-k

I took a look at the Blender Nation site linked to here

[quote=jonah1980]  	haven't checked it out yet but looks like native amd64 builds of blender are available below, how cool is that?

[http://www.blendernation.com/2006/07...ows-and-linux/](http://www.blendernation.com/2006/07...ows-and-linux/)[/quote]


On that page it explains what the various versions that person has compiled. This is why 

Athlon64 optimized for SSE2 **(32 bit mode)**
Its looking for a 32bit lib because its 32bit. 

Its possible the build you grabed that worked is in fact a 64bit version.

---

### Post by KhaaL on 2006-09-05
> **Kilz said:**
> 

Athlon64 optimized for SSE2 **(32 bit mode)**
Its looking for a 32bit lib because its 32bit. 

Its possible the build you grabed that worked is in fact a 64bit version.

Duh of the week, it was indeed 32bit package. I downloaded 2.41 from the repo and it worked fine (even under xgl+compiz, except for keyboard shotcut annoyances), however I'm really after version 2.42 since it uses the bullet engine...

Let me know if you get it working, Jonah :)

---

### Post by KhaaL on 2006-09-06
after a lot of blood, sweat and more tears, i got blender 2.42a working! I had to download it and all its dependencies (~20) from [http://packages.debian.org/](http://packages.debian.org/) since the ones in the repo are outdated. Only package I haven't updated is libsdl1.2debian so I forced the installation and blender shows up now as a broken package. However, rendering and the game engine seems to work fine. 

Yarr, time to plug in the wacom board and start to blend! ;->

EDIT: Ok, not having that package installed was a bad idea, x-server crashed while rendering... I'll have to add it and its dependencies later

EDIT2: No dice with installing libsdl1.2debian, it conflicted with ubuntu's version of libsdl1.2debian package and always show up as broken... Guess I'm stuck with blending on windows for now

---

