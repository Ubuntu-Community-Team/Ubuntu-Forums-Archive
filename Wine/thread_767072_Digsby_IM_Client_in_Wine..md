---
title: "Digsby IM Client in Wine."
date: 2008-04-25
forum: Wine
---

### Post by Aruza on 2008-04-25
While running windows for the last couple of weeks i have fallen in love with [Digsby]("http://www.digsby.com"). I have decided to again try the switch to linux, trying the new Ubuntu 8.04.
I found a guide which showed how to run digsby in Wine ([Here]("http://forum.digsby.com/viewtopic.php?id=381")) and tried that and Digsby will install and run, show the buddy list but no IM windows will pop up and no notifications will appear.

I am really hoping that someone out there has gotten this to work, so any help would be awesome.

I am running Ubuntu 8.04 like i said and wine version 0.9.59

Thanks!
Aruza

---

### Post by cogadh on 2008-04-25
It would appear that as of Wine 0.9.58, Digsby no longer works:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11408](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11408)

---

### Post by Aruza on 2008-04-27
Thanks to cogadh for your response. I was unaware that wine had a DB of programs and how they worked under specific versions. 

Besides that i would love to hear of any other peoples failures or success in getting this to work.

thinks i have tried. 
Installing a version of wine (0.9.57) that is know to have worked.
     - still for some reason would not allow IM windows to pop up. Think the problem is that im running 8.04
     - tried loading the newest wine, 0.9.60 on 8.04, and ran into a problem where phython25.dll would not load. i downloaded blender to get the python25.dll file. removed the error saying it couldn't load that library but digsby will not load at all. 

Any thoughts at all are welcome (flames not so much :))

---

### Post by Apreche on 2008-04-28
I just started running Windows on my new desktop, and I have also fallen in love with Digsby. I'm still running Ubuntu on my laptop, and will continue to do so. However, now all of the IM clients on Linux feel inadequate when compared with Digsby. The Digsby people are working on a Linux client, but it is very frustrating to wait. Any help getting this to work would be very appreciated. I am having the exact same problem with the python dll and such.

---

### Post by Aruza on 2008-04-30
Bump!

---

### Post by cthrax on 2008-05-02
I got just about as far with Hardy and 0.9.59.

---

### Post by kyleabaker on 2008-05-04
Still no good news on this?

---

### Post by kreutzman on 2008-05-22
I've had success after following these instructions...

[http://forum.digsby.com/viewtopic.php?id=381](http://forum.digsby.com/viewtopic.php?id=381)

I'm using Wine 0.9.59 btw.

---

### Post by kreutzman on 2008-05-22
Actually, that's a lie...it doesn't work.

Sorry.

---

### Post by Joraeim on 2008-07-07
I was successful using 8.04 and Wine version 1.1.0, I used winetricks to install gdiplus.dll and the .NET2.0 framework. I then installed Digsby and it worked just fine other than not liking to stay connected to the facebook chat.

---

### Post by Aruza on 2008-07-20
you are correct in that using winetricks allows digsby to install but i will cannot get the popup windows to work. i haev no IM windows at all.

---

### Post by e1eventh on 2008-07-24
> **Aruza said:**
> you are correct in that using winetricks allows digsby to install but i will cannot get the popup windows to work. i haev no IM windows at all.

Go to preferences>advanced and uncheck "hide new conversation windows"

Only two problems I'm having are new messages to me appear as very small windows in the top lefthand desktop corner.  Also, sometimes I cannot get the buddy list to reappear without restarting digsby.

---

### Post by e1eventh on 2008-07-27
Well, in my second install I can't get the damn thing to work.  I get the oft cited but not solved "python25.dll" error.  How frustrating.

---

### Post by e1eventh on 2008-08-01
> **e1eventh said:**
> Well, in my second install I can't get the damn thing to work.  I get the oft cited but not solved "python25.dll" error.  How frustrating.

bump.  Anyone know how to fix this?

---

### Post by Aruza on 2008-08-03
when you install use winetricks to install .net1 and then restart install .net2 then restart and install gdiplus.dll all using winetricks and then install digsby and if you are using 8.04 and the newest version of wine you shouldnt have a problem.

---

### Post by e1eventh on 2008-08-04
> **Aruza said:**
> when you install use winetricks to install .net1 and then restart install .net2 then restart and install gdiplus.dll all using winetricks and then install digsby and if you are using 8.04 and the newest version of wine you shouldnt have a problem.

Thanks a lot.  That did it for me.  Now of course wineserver is taking 50% of my CPU, but I guess I shouldn't be picky.

---

### Post by romancexplosion on 2008-12-16
> **Joraeim said:**
> I was successful using 8.04 and Wine version 1.1.0, I used winetricks to install gdiplus.dll and the .NET2.0 framework. I then installed Digsby and it worked just fine other than not liking to stay connected to the facebook chat.

facebook chat disconnects even when run natively... they seem to still be working the bugs out of that

---

