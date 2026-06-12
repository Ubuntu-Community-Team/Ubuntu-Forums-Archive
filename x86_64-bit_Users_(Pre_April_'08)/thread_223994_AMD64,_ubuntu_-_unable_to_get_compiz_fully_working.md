---
title: "AMD64, ubuntu - unable to get compiz fully working past quinn20"
date: 2006-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by falcon15500 on 2006-07-27
Hi all,

  I have had a completely working compiz for some time now, however the latest series of changes have got me stumped.  I am currently sitting with compiz_0.0.013-0quinn20, gcompizthemer-0.12.  If I try to upgrade to quinn21, my window decorations revert to defaults - however compiz effects still work.  If I upgrade to quinn25, compile/install cgwd and upgrade gcompizthemer to 0.20 - I can't get any window decoration.

  I have tried changing my compiz-start.py to use cgwd, but I am not really sure what I am supposed to be doing.  If we are now using cgwd, do we killall gnome-window-decoration, start cgwd AND start compiz?  Or just start cgwd?  If so, what options?  --replace?  --replace gconf?

  Any ideas would be appreciated!

falc

Online

---

### Post by patbuntu on 2006-07-27
I tried this last night but didn't get too far.  I was using [this]("http://ubuntuforums.org/showthread.php?t=222034") thread, but it seemed that some of the packages were not available for amd64.

The suggestion was to use [these]("http://ubuntu.systemadministrator.org/dists/dapper/eyecandy/") packages, and that the above guide should then work.  I'm going to try this tonight when I get home, so any advice would be welcome.

-Pat

---

### Post by srikat on 2006-07-27
pat, thanks for pointing to that thread. I followed the directions and got it working. 

See [http://ubuntuforums.org/showpost.php?p=1307590&postcount=31](http://ubuntuforums.org/showpost.php?p=1307590&postcount=31)

I jotted down the steps briefly at [http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D](http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D)

---

### Post by falcon15500 on 2006-07-27
Thanks guys.  I rolled back the packages I had compiled/installed and installed the packages from those new repo's.  Worked like a charm and I have my bouncy stuff happening again. ;)  It's amazing how much I missed having fluid window physics...
 
I am at a loss to explain why my hand rolled packages didn't work.  Perhaps I had some missing libs or something, but nothing that was listed as a dependency?

<shrug> In any case, I am happy now.  Again thanks.

falc

---

### Post by John.Michael.Kane on 2006-07-28
falcon15500 you manage to get compiz/xgl working under 64bit ubuntu great.

---

