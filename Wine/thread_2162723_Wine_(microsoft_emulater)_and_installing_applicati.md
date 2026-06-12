---
title: "Wine (microsoft emulater) and installing applications for use"
date: 2013-07-15
forum: Wine
---

### Post by CrimsonDragon on 2013-07-15
I have installed wine and am trying to install IndraWorksDs software but cannot get it to launch ... I am having the same problem trying to install Rift ... can anyone provide some direction ... thanks in advance ...

---

### Post by oldos2er on 2013-07-15
Moved to Wine.

I searched appdb.winehq.org for "IndraWorks" but couldn't find anything useful, which is not a good sign.

---

### Post by Paqman on 2013-07-15
IndraWorks doesn't seem to be listed in the [WineAppDB]("http://appdb.winehq.org/"), but [Rift]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22884&iTestingId=78627") is. It sounds like it works, but does occasionally crash on launch.

---

### Post by lukeiamyourfather on 2013-07-15
Your title says emulator, that's not what Wine is (Wine = Wine Is Not an Emulator). It's a compatibility layer with a partial feature set, if the application you need makes a call for a feature that isn't implemented there will be issues. That's why some applications work fine with Wine and some don't. If your application doesn't work with Wine (or doesn't work well) consider using a virtual machine like VirtualBox where you can run Windows inside of Linux and most applications that don't like Wine become fully functional that way.

---

### Post by CrimsonDragon on 2013-07-15
Ann - Sorry for posting it in 'absulutely beginner' but I do think that it speaks for itself ... The beginner part at least ... 

Paqman - ty I will have to check into it ... 

lukes father -- mischoice of words, there are times that I am lucky if I can remember my name, old dog learning new tricks and what a ride ... I was hoping I would be able to 
run them clean in wine but it seems that I have a learning curve ... thanks to all ...

---

### Post by CrimsonDragon on 2013-07-15
Hello again -- I managed to get Indra works running, what I did was removed wine, deleted the desktop icon for IndraWorks,
 reinstalled wine, wine tricks and Microsoft Compatibility layer (Meta Package), I then reinstalled the IndraWorks Package ...
 I will more that likely set it you on a VM because it requires use of a usb-serial adapter. Much thanks to all for the help ...

---

