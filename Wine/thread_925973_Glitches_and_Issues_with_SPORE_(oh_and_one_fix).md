---
title: "Glitches and Issues with SPORE (oh and one fix)"
date: 2008-09-21
forum: Wine
---

### Post by Sugi on 2008-09-21
When my game close sometimes either crashes or I exit out of the game, the resolution of Ubuntu gets set to whatever the game's resolution was.  How do I fix these glitches and bugs?


SPECS:
Ubuntu Hardy Heron 8.04
Self Compiled Wine 1.1.5
No-CD Patch for Spore
All Graphic Settings: High
Except Depth of Field: Lowest (I heard this fixes crashes)

UPDATE:  I have gotten some of the bugs fixed either from appdb or #winehq.  Here are some Issues and fixes:


Issue:
I have an odd river glitch in the middle of my game.  It's there in safe mode and settings set to high.
High Settings:
[http://ubuntuforums.org/attachment.php?attachmentid=85974&stc=1&d=1222017136]("http://ubuntuforums.org/attachment.php?attachmentid=85974&stc=1&d=1222017136")
Safe Mode:
[http://ubuntuforums.org/attachment.php?attachmentid=85976&stc=1&d=1222017136]("http://ubuntuforums.org/attachment.php?attachmentid=85976&stc=1&d=1222017136")

Issue:
I have this odd hanging shadow in game. Wherever I go, it goes.
[http://ubuntuforums.org/attachment.php?attachmentid=85975&stc=1&d=1222017136]("http://ubuntuforums.org/attachment.php?attachmentid=85975&stc=1&d=1222017136")

> The Fix for River glitch and Odd shadow:
Wine regedit
HKEY_CURRENT_USER>Wine>AppDefaults>SporeApp.exe>Direct3D
String Vaule
Name it "OffScreenRenderingMode" with a vaule of "fbo"
Exit

NOTE: You may to need create a new key for "SporeAppe.exe" and "Direct3D".  Though this is nice because these registry edits WON'T affect other wine games.



Issue: While in tribal mode of the game, I scroll over to see the other tribe and I use the middle click to rotate and this causes the game crash only at this point though.
Terminal Output:
Backtrace:
```
=>1 0x7df4cd9e (0x3fa6a1cc)
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
```

> The Fix:
cd /path/to/location/of/SPORE/Sporebin/
wine SporeApp.exe -safe
and/or
env WINEDEBUG=-all wine SporeApp.exe

I personally have not seen anything different from WINEDEBUG, but others have said it helps.

NOTE: I was able to run the game bigger than 800x600.  But if i change any of the graphic settings, it causes the game to crashes.

NOTE:
If you get a lot of crashes after mating and creature creation.  Try setting your Graphic Cache Size to 768 MB (or at least lower then it's default.) IE: For me the default Graphic Cache Size was set to 1024 MB and I lowered it to 768 MB.  My game stopped crashing after mating calls.

The Graphic Cache Size was the same issue Windows user were having.o.0


Sugi

---

### Post by aoanla on 2008-09-21
The odd river glitch is known about:

[http://bugs.winehq.org/show_bug.cgi?id=15205](http://bugs.winehq.org/show_bug.cgi?id=15205)

a suggested workaround is to set your OffscreenRenderMode to 'fbo' in the Wine registry.

Your shadow and crash issues are also known about, and are mostly fixed in Wine 1.1.5 - I suggest you upgrade if you haven't already.

I also suggest that you follow the AppDB entry (and related bug pages) for Spore to see if people have any other help for you:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652)

---

### Post by Sugi on 2008-09-21
That's odd.  I am using Wine 1.1.5 self compiled as well. :-/  I will try the fixes for the shadow and the river glitch.

Thanks,
Sugi

---

### Post by Sugi on 2008-09-22
I got the river glitch fixed by using OffscreenRenderingMode set to fbo.  And most of the crashes has stopped because I ran spore within safe mode.  But Spore looks like crap now.  Has anyone got Spore to work with anything set higher then Low settings??

---

### Post by Baender on 2008-09-26
I installed Spore under Ubuntu 8.04 via Wine 1.15. With adding the fbo value in the registry, i run Spore with high graphic setting without any problems. I use a no cd patch to avoid a own Winecompilation, this progress is to difficult for me.

The Game runs fine, except for the invisible creatures.

I installed the ATI graphics driver via ENVY, i guess it installed the 8.42.3 catalyst version. I' m not able to compile a newer driver, because i always get a black screen after the reboot. Maybe it's because of the graphiccard which is a AGP version of the Radeon 2600 HD.

Does anyone have an idea how to fix the problem with the invisible creatures?

---

### Post by Guilou on 2008-09-27
I'm using Ubuntu Hardy Heron on a laptop with an ATi Card (X200Mobilty).
I would like to try Spore on Ubuntu using Wine 1.1.5.

The first time I launched the game, everything was black. I just can hear sounds, and see the mouse cursor.

I've installed the latest ATi drivers, and add the "fbo" value to wine's registry.

Now, I can see menus, but my creature is invisible !

This problem of invisible creature appears with ATi cards. Someone have a workaround ?


(Sorry for my English, it's not my native language)

---

