---
title: "Fonts problems in Photoshop CC"
date: 2014-05-29
forum: Wine
---

### Post by Adiost on 2014-05-29
I spent an enormous amount of time trying to make Photoshop CC work in wine, finally did it with PlayOnLinux. I installed mstftfonts, installed allfonts and gdiplus using winetricks, I also copied fonts from fresh Windows installation to wineprefix/photoshop/drive_c/windows/fonts.

No matter what I try fonts are corrupted. Default Windows forms work fine in Photoshop (menus), but any additional windows (preferences, create new file, splash window, image settings etc.) are missing fonts. Also the top bar looks very corrupted, I have absolutely no idea how do I fix it, I tried everything I can, but I can't get fonts working, even though there are many successful reports on winehq.

I'm a linux newbie, running Kubuntu 14.04, what should I try to fix that?

Screenshot:
[http://i.imgur.com/IP8wAc2.png](http://i.imgur.com/IP8wAc2.png)

---

### Post by joska2 on 2014-06-02
Having the exact same issue. The Photoshop splash screen doesn't display the credits text on load either. I've tried with Wine 1.7.13 and 1.6.2 on Ubuntu 14.04. 

Followed these instructions [http://evertheylen.appspot.com/blog/photoshop-in-linux](http://evertheylen.appspot.com/blog/photoshop-in-linux) to the tee. 

Have installed the following libraries in Play on Linux:


[LIST]
[*]atmlib
[*]corefonts
[*]msxml3
[*]msxml6
[*]gdiplus
[*]vcrun2010
[*]allfonts
[/LIST]

And migrated my fonts from my Windows installation as well. 

[http://i.imgur.com/xmTCKKr.png](http://i.imgur.com/xmTCKKr.png)

---

### Post by wizkidweb on 2014-08-22
I am also having the same problem exactly.  Everything works but I can't even work with projects with many layers because I can't see their names.  Running wine 1.7.24 on Ubuntu 14.04 through PlayOnLinux.

I've installed all of the libraries in the post above, but allfonts wouldn't finish installing as there was a timeout downloading one part, but just in case, I copied the fonts from my Windows installation.

[IMG]http://i.imgur.com/bxf9zL1.png[/IMG]

Anyone have any idea what could be causing this?

---

### Post by Svetlozar_Georgiev on 2014-09-09
Installing *allfonts *with* winetricks *fixed this for me*. *Using wine 1.7.26.[IMG]http://i61.tinypic.com/1p9zmd.png[/IMG]

---

### Post by dgeorgiev on 2014-09-21
Svetlozar_Georgiev can you specify your wine settings and what else have you installed ?

---

### Post by Svetlozar_Georgiev on 2014-10-09
I believe I followed this guide -> [http://evertheylen.appspot.com/blog/photoshop-in-linux](http://evertheylen.appspot.com/blog/photoshop-in-linux)

---

### Post by superyoche on 2014-10-12
Hi!

I'm having the same issue..

Svetlozar_Georgiev, which version of Ubuntu are you using?

I suspect Photoshop CC not working properly on Ubuntu 14.04..

---

### Post by Svetlozar_Georgiev on 2014-10-22
I am using exactly 14.04

---

### Post by mesonoxianvlad on 2014-12-28
Hi guys.

I had the same problem.

After a whole day of research I found out it could be caused by having two copies of the same font.

So what I did was install only vcrun2008 msxml3 atmlib gdiplus vcrun2005 vcrun2005sp1 using winetricks without installing any fonts.

The result was positive and the problem went away.

I guess it might be because installing extra fonts might mess with the fonts included with photoshop.

Hope this helps.

OS:
Elementary OS Freya 64bit (Based on Ubuntu 14.04)
Wine 1.7.33 32bit

[ATTACH=CONFIG]258838[/ATTACH]

---

