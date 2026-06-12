---
title: "Wine - DirectX 9?"
date: 2005-06-21
forum: Wine
---

### Post by sbm on 2005-06-21
Hi

I've tried to figure out how to patch wine with the patch from:
[http://sourceforge.net/projects/directxwine/](http://sourceforge.net/projects/directxwine/)

It is a .diff file.
How do I patch the wine source before compilation?

Would be so cool to get directX running in wine. Would love to play everquest II in ubuntu :-)

/SBM - Playing on RunnyEye btw

---

### Post by sbm on 2005-06-22
Someone must know :-)

Can't find any info on the subject on the sourceforge page.

---

### Post by nocturn on 2005-06-22
I think you need to use the pach command.
Untar the wine source, copy the diff file to the same dir and change to that dir.

I think patch <nameofpatch.diff should do it (man patch can help).

---

### Post by sbm on 2005-06-22
patch <patchfile.diff> seems to run. It does never end though.
Otherwise the runtime for that proces is huge :) Doubt it though, since the patch file is rather small.

Has been running for 30min now, without harddisk activity.

/SBM

---

### Post by sbm on 2005-06-22
Solved it.

I used patch in a wrong way. Correct use to apply patch:
  
  patch -p2 < (path_to_patch)/<patch>.diff

Now crossing my fingers to get directx running correctly :-)

/SBM

---

### Post by Moobert on 2005-06-22
theres also a nice auto building script for many wine versons, found at:
[http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)

---

### Post by FoxHappy on 2007-12-03
> **sbm said:**
> Solved it.

I used patch in a wrong way. Correct use to apply patch:
  
  patch -p2 < (path_to_patch)/<patch>.diff

Now crossing my fingers to get directx running correctly :-)

/SBM

In the exact same situation you were smb. Mind you I think this post is like over 2 years old, but, where exactly is the path to patch it to, and did this work for you?

---

