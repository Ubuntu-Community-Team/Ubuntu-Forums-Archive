---
title: "Problems building blender"
date: 2008-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by henkm on 2008-03-14
I'm trying to build blender on ubuntu 7.10 on my dual core.
I have download the blender-2.45 source files
I searched everywhere for the necessary dependencies. 
I tried to build blender with scons, according to 
[http://wiki.blender.org/index.php/Blender_3D:_ActionBook/Blender_Compiling]("http://wiki.blender.org/index.php/Blender_3D:_ActionBook/Blender_Compiling")

Yet the following errors appear:
> Compiling ==> 'BSP_MeshPrimitives.cpp'
Linking library ==> 'libblender_BSP.a'
Compiling ==> 'FTGlyphContainer.cpp'
In file included from extern/bFTGL/src/FTGlyphContainer.cpp:1:
extern/bFTGL/include/FTGlyphContainer.h:4:22: error: ft2build.h: No such file or directory
extern/bFTGL/include/FTGlyphContainer.h:5:10: error: #include expects "FILENAME" or <FILENAME>
extern/bFTGL/include/FTGlyphContainer.h:6:10: error: #include expects "FILENAME" or <FILENAME>
extern/bFTGL/src/FTGlyphContainer.cpp:30: error: expected ‘,’ or ‘;’ before ‘{’ token
extern/bFTGL/src/FTGlyphContainer.cpp: In member function ‘FTPoint FTGlyphContainer::Render(unsigned int, unsigned int, FTPoint)’:
extern/bFTGL/src/FTGlyphContainer.cpp:85: error: ‘class FTFace’ has no member named ‘Error’
scons: *** [/home/henk/compile/build/linux2/extern/bFTGL/src/FTGlyphContainer.o] Error 1
scons: building terminated because of errors.


Does somebody have a clue

---

### Post by Kilz on 2008-03-14
Do you have ftgl-dev installed.

---

### Post by henkm on 2008-03-14
ftgl-dev was missing.

Seems you a lot of -dev files

I'm still moving on know, each time finding errors and installing other dependencies

Where can I find the complete list with dependencies??

---

### Post by henkm on 2008-03-15
I'm some steps further.

Now I have the following error:
I use  " scons WITH_BF_VERSE=1 WITH_BF_OPENAL=0" 

> Compiling ==> 'buildinfo.c'
Linking program ==> 'blender'
/usr/bin/ld: cannot find -lXi
collect2: ld returned 1 exit status
scons: *** [/home/henk/compile/build/linux2/bin/blender] Error 1
scons: building terminated because of errors.


Somebody some suggestions??

---

### Post by Kilz on 2008-03-15
> **henkm said:**
> ftgl-dev was missing.

Seems you a lot of -dev files

I'm still moving on know, each time finding errors and installing other dependencies

Where can I find the complete list with dependencies??

You can try 
```
sudo apt-get build-dep blender
```
To install the build dependencies.  I have never compiled blender, I just use the one in the repositories. Not sure about the error above this post.

---

### Post by henkm on 2008-03-24
I succeed in building blender 2.45 on ubuntu 7.10 64 bits

Thank you people!!!

---

