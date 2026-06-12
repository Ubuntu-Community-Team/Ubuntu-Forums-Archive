---
title: "d2gs.exe thru wine on a server"
date: 2008-11-30
forum: Wine
---

### Post by lunaz on 2008-11-30
i'm trying to get d2gs.exe working for diablo lod 1.09d by following this guide:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9597](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9597)

this guide assumes i have a gui, but my server does not. i compiled wine 0.9.49 --without-x & --without-opengl but it still apparently wants to use the x11 drivers.

i do wine D2GS.exe & i get this error:

err:imagelist:ImageList_ReplaceIcon no color!

the instructions i see everywhere have to do with ~/.wine/config, but my wine didn't come with one. creating one did no good. i can't use regedit w/o a gui apparenly, i don't know how to use the .reg files in ~/.wine either.




if there's no hope for getting this working w/o gui, how do i use a MINIMAL gui on a server AND get it working w/ wine?

---

