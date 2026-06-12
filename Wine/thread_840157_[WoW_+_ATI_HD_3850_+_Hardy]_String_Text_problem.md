---
title: "[WoW + ATI HD 3850 + Hardy] String Text problem"
date: 2008-06-25
forum: Wine
---

### Post by Raum on 2008-06-25
Hello,

I've update my Ubuntu Gutsy to Hardy (7.10 -> 8.04) and Wine 0.9.somthing to wine-1.0-rc4. I've the lastest ATI proprietary driver installed.

Before, I could run WoW without any problem in OpenGL except the buggy minimap when I entered in a closed area map (a tavern, or a cavern, etc.), the minimap became blank... (before: Gutsy, Wine 0.9.6x, ATI Catalyst 8.1, after: Ubuntu Hardy 8.04, Wine 1.0rc4, ATI Catalyst 8.4, ATI HD3850).

Now, when I enter in a closed area, I've something like :
[[img]http://graagb.free.fr/mini_text_prb.jpg[/img]](http://graagb.free.fr/text_prb.jpg)


It's very annoying Rolling Eyes

Only the first character of a string is displayed, the rest of the string is bugged.

When I get out of the area, I need to reinitialize my video configuration (by changing antialising for example) and I recover a good image without error. When I enter again in a closed area, the screen is bugged again...

I've changed to Direct3D and I've a lot of errors (vanished walls, etc) but the strings appear normal.

Do you have an idea ? I've posted on [WineHQ Forum](http://forum.winehq.org/viewtopic.php?t=1283) but without any clue... 

Thanks

---

### Post by tehpyrate on 2008-06-25
I had that problem when I installed WoW WINE the first time on Linux. I think its the 8.4 ATI Drivers that may cause it. 

Check this out: 

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Follow those instructions exactly and your ATI Driver installation should work pretty flawlessly...aside from the Usual Garbage that comes with ATI Drivers.

Then I suggest you reinstall WINE using these instructions:

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Should Make things work.. alot better

I've got a X2900XT myself and ..well I just wish I got better performance out of mine =/

---

### Post by multiboot on 2009-05-15
You should check out this thread:

[http://ubuntuforums.org/showthread.php?p=6246894](http://ubuntuforums.org/showthread.php?p=6246894)

I had the same exact problem running 8.04 with a radeon x1600 and now I'm running smoothly after performing a simple wine registry edit.

---

