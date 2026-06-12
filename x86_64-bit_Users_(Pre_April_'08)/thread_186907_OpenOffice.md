---
title: "OpenOffice"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by kurbacik on 2006-06-02
Does anybody know why OpenOffice doesn't appear in the Applications menu even though through Synaptics it is clearly labelled as installed?

---

### Post by JoWilly on 2006-06-02
[QUOTE=kurbacik]Does anybody know why OpenOffice doesn't appear in the Applications menu even though through Synaptics it is clearly labelled as installed?[/QUOTE]

Works fine here.

Have you just installed it ? Then try to log out or do a "killall gnome-panel".

---

### Post by meng on 2006-06-02
Or else go to your menu editor and see if the openoffice shortcuts are there but disabled.

---

### Post by kurbacik on 2006-06-02
[QUOTE=meng]Or else go to your menu editor and see if the openoffice shortcuts are there but disabled.[/QUOTE]

I have tried both previous solutions but with no luck. If I knew where the executables were located I could create the links myself to the application menu.

---

### Post by JoWilly on 2006-06-02
[QUOTE=kurbacik]I have tried both previous solutions but with no luck. If I knew where the executables were located I could create the links myself to the application menu.[/QUOTE]

/usr/lib/openoffice/program/


But this should not happen. Have you tried reinstalling it ?

---

### Post by kurbacik on 2006-06-02
[QUOTE=JoWilly]/usr/lib/openoffice/program/


But this should not happen. Have you tried reinstalling it ?[/QUOTE]

I just resintalled OpenOffice. The upgrade to Drapper just erased the previous installation of OpenOffice. Has anybody else noticed this strange behavior?

---

### Post by meng on 2006-06-02
Yes it happened to me too, and many others IIRC. But from the OP, I was led to believe that you had already reinstalled it. Never mind, so long as it works now!

You may find that OpenOffice Draw is in the Graphics section rather than the Office section of the menu. Simply fixed with menu editor. Also my OpenOffice Math disappeared - I'm not certain if it is an independent component anymore.

---

### Post by kurbacik on 2006-06-02
[QUOTE=meng]Yes it happened to me too, and many others IIRC. But from the OP, I was led to believe that you had already reinstalled it. Never mind, so long as it works now!

You may find that OpenOffice Draw is in the Graphics section rather than the Office section of the menu. Simply fixed with menu editor. Also my OpenOffice Math disappeared - I'm not certain if it is an independent component anymore.[/QUOTE]

Thanks for the help. I was making a mistake believing that it was installed while it wasn't. OpenOffice Math isn't present anymore here either.

---

### Post by meng on 2006-06-02
It's still a component, as you can insert an equation in Writer (now Word Processor). But the help file refers to a more detailed help file in Math - as though it were an independent component still - of course they could have been sloppy with editing the help file.

---

