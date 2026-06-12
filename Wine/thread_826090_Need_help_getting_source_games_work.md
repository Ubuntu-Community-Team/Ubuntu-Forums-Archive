---
title: "Need help getting source games work"
date: 2008-06-11
forum: Wine
---

### Post by icouldntfindausername on 2008-06-11
I'm using Arch Linux and Wine 1.0rc4. I'm trying to get my steam games to work. This includes Half Life 2, Portal, Team Fortress 2 etc. However, when I try to start one of them through steam, none of them will work. At first the game actually booted when I added -dxlevel 80 or -dxlevel 81, but the graphics were all garbled, even in the menu. See picture below:

[IMG]http://img355.imageshack.us/img355/3193/screenshotyc7.png[/IMG]

I then tried adding -dxlevel 9. This time I got a proper screen when I started it up, but then I got this message: "your graphics hardware must support at least pixel shader version 1.1 to run this game". Does anyone know why I get this?

My graphics card is 8800 Ultra and I'm using 169.12 drivers. I also installed directx 9.0c, and all the dxdiag tests work as they should.


Thanks :)

---

### Post by Meow27 on 2008-06-11
installing direct x 9 might have bee na bad idea since Wine already has its own included.

just my 2 cents, i dont have any steam games so i cant help you there :/

---

### Post by Sleaka J on 2008-06-11
Installing DirectX into Wine is bad for Wine. Wipe it and start again.

---

### Post by icouldntfindausername on 2008-06-15
Ok, I completely reinstalled Arch Linux and a fresh install of WINE 1.0 rc5 and 169.12 nvidia drivers. Now Half Life 2 and Counter Strike Source start, but I only get like 5-10 fps. Why is that? With my computer I should get way more than this. I tried running the command "glxgears", and I got a result of 28 000 fps. Is there a setting or something I need to change in order to improve my fps? This is getting sort of frustrating...

Thanks!

---

### Post by RESID3NT on 2008-06-15
> **icouldntfindausername said:**
> Ok, I completely reinstalled Arch Linux and a fresh install of WINE 1.0 rc5 and 169.12 nvidia drivers. Now Half Life 2 and Counter Strike Source start, but I only get like 5-10 fps. Why is that? With my computer I should get way more than this. I tried running the command "glxgears", and I got a result of 28 000 fps. Is there a setting or something I need to change in order to improve my fps? This is getting sort of frustrating...

Thanks!

Welcome to my Ubuntu hell. :lolflag:
I got 30-70's, with HUGE breaks, when in Vista x64 I have no less than 100 in every map!
I'll try to see if 64bit Ubuntu does well for me.

I'll post a reply here.

---

### Post by icouldntfindausername on 2008-06-15
Thanks for your reply. In Vista X64 I obviously get great fps with no problems at all. However, in Arch Linux X64 (which I'm using now) it just won't work well. I never get high fps with huge drop downs like you seem to suffer. My fps is stable around 5-10 fps... Not playable in other words :(

---

### Post by DDJ on 2008-06-15
> **Sleaka J said:**
> Installing DirectX into Wine is bad for Wine. Wipe it and start again.

i installed DirectX 9c and it works fine with WINE.  I used the howto located at [http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html](http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html)

---

### Post by dmn_clown on 2008-06-15
> **icouldntfindausername said:**
> Ok, I completely reinstalled Arch Linux and a fresh install of WINE 1.0 rc5 and 169.12 nvidia drivers.

For future reference, re-installing the entire operating system is not the best way of fixing a problem.  In your case the simplest solution would have been to rm -rf ~/.wine after backing up your windows programs.

Also, why are you asking for Arch support on an Ubuntu forum?  I would imagine that the best support for Arch would be found on the Arch Forums: [http://bbs.archlinux.org/](http://bbs.archlinux.org/) or the Arch mailing lists: [http://www.archlinux.org/mailman/listinfo/](http://www.archlinux.org/mailman/listinfo/)

---

### Post by icouldntfindausername on 2008-06-15
I chose to ask here simply because I wouldn't have thought there would be any difference between arch and ubuntu in this case, but that the problem rather was related to wine or something like that. But I wouldn't know...

---

### Post by Fred_E _krugar on 2008-06-15
Ok first of try one thing before you give up I my self have my 8800gt OC'ed to 725 and my Core2Quad oc'ed to 3.45Ghz and I have to keep my resolution at 1280 X 900 (22inch SAmsung). The only time I experience drops like you are talking about is in games with more than 32 people.

Now dont say it is my connection cause I have 6meg down 1.5meg upload, and my ping on the severs I play do not have over 25ms.


So what I am saying is to try and turn you resolution down and try a game with less than 32players. The Legion on dust2 works good for me most all the time give them a try and let me know. Hell I might even be on there just Look for me or my grandson I am (A 5 A$$ed Monkey) grandson is Dooshbag. Well happy fraging.

---

### Post by icouldntfindausername on 2008-06-16
I'm running 640x400 and all settings at low... Single player as well. :confused:

---

### Post by dmn_clown on 2008-06-16
[QUOTE=icouldntfindausername]Now Half Life 2 and Counter Strike Source start, but I only get like 5-10 fps. Why is that?[/QUOTE]

Because DX9 performance of the source engine through wine isn't the greatest.  Follow the howto here:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2890](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2890) but use -dxlevel 81 for better FPS.

---

