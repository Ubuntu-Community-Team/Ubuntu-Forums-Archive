---
title: "master of orion 2 not launching"
date: 2007-12-09
forum: Wine
---

### Post by luke16 on 2007-12-09
Anyone else have master of orion 2 with wine .9.50? Mine will install, but wont launch at all. The install didn't even put a shortcut in the wine 'start menu', and nothing at all happens when I double click on the .exe. I even tried telling wine to use windows 95 compatibility when launching the thing.

And as for the patch, it's basically a zip file that wants you to extract its contents into the main game directory, saying that it will overwrite some files, but it won't overwrite anything because linux doesn't ignore capitalization like windows does. The files just end up added to the directory.

---

### Post by steevols on 2007-12-09
You could poke around at the WineHQ AppDB and see what you come up with. I know absolutely nothing about the game, but this might help:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=210&iTestingId=16110](http://appdb.winehq.org/objectManager.php?sClass=version&iId=210&iTestingId=16110)

---

### Post by lavinog on 2007-12-09
I have yet to install it in linux, but i hear that the best way to run it in linux is with dos box

---

### Post by cogadh on 2007-12-09
Only if you have the DOS version. If you are trying to run the Win 95 version, then Wine is the way to go.

You might also want to check out [FreeOrion](http://www.freeorion.org/), an open source game "in the tradition of the Master of Orion series". Its still in beta, but it looks pretty good.

---

### Post by lavinog on 2007-12-10
I have the windows version, It has a separate executable for loading from dos.
I need to try free orion again...moo2 is the best...what were they thinking when they made moo3?

---

### Post by luke16 on 2007-12-10
I thought that the only version was the cd that installs both executables. But considering that the win95 version doesn't even launch (or even give out any error messages) or get its own menu shortcuts for wine, I was hoping that there is at least some way to begin to fix this. At least without messing around with dos *shudders*. I'm not much of a dos person.

---

### Post by lavinog on 2007-12-11
check out this page [http://masteroforion2.blogspot.com/2006/05/dosbox-guide.html]("http://masteroforion2.blogspot.com/2006/05/dosbox-guide.html")

i did notice that the moo2 download may not have dos support.

I think I will try to install it with wine tomorrow after my last final
I will post back if i can get it to work.
> At least without messing around with dos *shudders*. I'm not much of a dos person.
How are you with linux then? I would think if you can handle linux shell commands you should be able to handle dos (i think the main difference is you use backslash in dos instead of forward slash.

---

### Post by luke16 on 2007-12-11
> **lavinog said:**
> check out this page [http://masteroforion2.blogspot.com/2006/05/dosbox-guide.html]("http://masteroforion2.blogspot.com/2006/05/dosbox-guide.html")

i did notice that the moo2 download may not have dos support.

I think I will try to install it with wine tomorrow after my last final
I will post back if i can get it to work.

How are you with linux then? I would think if you can handle linux shell commands you should be able to handle dos (i think the main difference is you use backslash in dos instead of forward slash.

Thanks for reminding me about finals. I think...
I'll see if you can get yours working and finish with my own finals before I try messing around with dosbox.
As for my hate with dos, its not that I hate it because its a command line interface, I hate it because its a HORRIBLE command line interface. What with the IRQ, "extended memory" and all that other crud that you have to put up with, at least when your working with real dos on an old machine, and not just an emulator.

---

### Post by luke16 on 2007-12-13
While it looks like it CAN run on dosbox, I would much rather get it working under wine. There is no sound with dosbox and it is a royal pain dealing with even getting the config file working. 

It looks like wine can't initialize the graphics in 8 bit color mode. I would assume that I would have to make a change to xorg.conf to correct this or maybe find a way to force wine to not be so bitchy about it, but I don't know how to do either.

```
$ wine "C:\Program Files\Microprose\Orion2\ORION95.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x33f8cc,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
```

---

