---
title: "[SOLVED] Running powerpoint installed in XP"
date: 2008-10-23
forum: Wine
---

### Post by kaspar_silas on 2008-10-23
Hi all,

I am trying to run microsoft office applications (powerpoint is the only one that I really care about) under wine. The applications were all installed under XP. I thought I would be able to mount the windows partition, go to the .exe files and run under wine. 

However no matter what I try I keep getting this IOPL not enabled message error message.

I have tried various suggestions I found to fix this such as: 
-Setting export WINEPREFIX="/home/myname/.wine"
-Using winetricks to install dcom98
-Using winecfg to set gdiplus(native,builtin)

But all to no avail, as such I am considering getting  an installation disk and reinstalling under wine. However this is a pain for me, so I thought I would ask if this is likely to do any good. Has anyone solved a similar problem by doing this before.

If anyone can reply with any advice or links to tricks I missed it's very much appreciated.

---

### Post by kaspar_silas on 2008-10-24
So just to clarify, noone has solved a wine issue by installing through wine.

---

### Post by kerry_s on 2008-10-24
[http://appdb.winehq.org/appview.php?appId=31](http://appdb.winehq.org/appview.php?appId=31)

---

### Post by kaspar_silas on 2008-10-24
Thanks for the reply but naturally I did actually look at winehq first. 

However my question was if my iopl problem is at all likely to be solved by the differing install type. Basically all I want to know is if a install through wine is at all different to running wine on an XP installed program. 

Because if it is not it seems a waste of my time doing it. That said I ordered the install disk anyway.

---

### Post by kaspar_silas on 2008-10-29
Just to let you all know installing through wine solved the problem.

---

