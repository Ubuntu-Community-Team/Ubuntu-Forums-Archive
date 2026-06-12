---
title: "Joint-post- tf2 black screen with minimal features/text showing"
date: 2011-12-04
forum: Wine
---

### Post by uh20 on 2011-12-04
because me and gardengxc were both idiots and posted the exact same problem next to each other under gaming&leuisure, ive decided copy-ing the posts as a joint

this problem occurs both with playonlinux and wine w/steam's installer.

gardengxc:running Ubuntu 10.04 with a EVGA GeForce 8600 gts.
                dxlevel 81 trick only makes the issue worse. 

uh20:running Ubuntu 10.10 with Nvidia Quadro FX 1400
        Had the game running fine a month ago with supposed same settings
        a quick check shows wine is using the video drivers correctly

there is a file called patch.diff that could fix this  problem, instructions on this patch would be helpful
these are images as posted by gardengxc, my image is simmilar in that its basically the pieces from the dx9 and dx8.1 images combined
Using DX9.0
[IMG]http://oi40.tinypic.com/4gsmx3.jpg
Using DX8.1
[IMG]http://oi41.tinypic.com/ke6bzb.jpg
this is a copy over of this post: [http://ubuntuforums.org/showthread.php?t=1890873](http://ubuntuforums.org/showthread.php?t=1890873)
it was in the wrong forum and thus i moved it here adding in my information,
edit:i dont know how to thumbnail!

---

### Post by jakejw93 on 2011-12-04
Having the same problem mate, can you run native games at all? I've tried and they haven't worked..

---

### Post by jakejw93 on 2011-12-04
I take that back, tried the binding of isaac and it worked

---

### Post by DoktorSeven on 2011-12-04
According to wine appdb some have had success with adding -nod3d9ex -- trying it with mine now.

Edit: -nod3d9ex added to the launch options of TF2 (right click game->Properties->Set Launch Options).  And it does indeed fix mine, TF2 plays perfectly! :)

---

### Post by gardengxc on 2011-12-04
Thank you that seems to work.

---

### Post by uh20 on 2011-12-04
im yet to test if this helps (im phone-posting), but i feel stupid because i partly read that topic without pressing the reply by:'s

---

