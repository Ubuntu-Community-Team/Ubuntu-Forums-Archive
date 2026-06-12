---
title: "Beryl drawing black screens on U7.04"
date: 2007-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_spiff on 2007-05-04
Hey, I installed beryl, and seems to work fine, except that sometimes it doesnt draw the gui. like I start the rythmbox player, it instead draws just a black space with a outline! :(. Anyone else having this issue?:( attached a thumbnail.


I checked out on the irc channels and someone suggested to right click on the beryl 'system tray' icon, > Advanced Beryl Options>Rendering Platform> click on force AGLX.
I think is a workaround for nvidia only. Someone check out.

---

### Post by Tanker Bob on 2007-05-05
This is a known bug in the NVIDIA drivers.  NVIDIA is actively working on the solution, but personally I think that something in Beryl contributes to the problem.  You can read about it [here](http://www.nvnews.net/vbulletin/showthread.php?t=84562&page=10).  A workaround that I'm currently using, courtesy of djdoo on that NV forum, is as follows:

In /etc/X11/xorg.conf add these lines:
```

Under "Screen" section:
Option "TripleBuffer" "True"
Option "BackingStore" "True"
Option "DisableGLXRootClipping" "False"
Option "AllowGLXWithComposite" "True"

Under "Extensions" section:
Option "RENDER" "Enable"
Option "Composite" "Enable"

```
Some have had problems with the BackingStore setting, but it works fine here.  If it causes problems, just delete that line.  In addition, you should set the following in the Beryl Manager's Advanced Beryl options:
```

Render path "Texture from Pixmap" 
Composite Overylay Window "Don't Use Cow" 
Render Platform "force AIGLX" 
Binding "XGL binding" 
Rendering "XGL rendering"
```
The combination of all these settings preserves the performance of the driver but eliminates the black window bug.  Hope this works out for you.

---

### Post by Alex&amp;Linux on 2007-06-04
Heyo,
This problem sucks, and this fixed it:

1. Open "beryl-manager"
2. "Advanced beryl options"
3. "Rendering path"
4. Choose "Copy" instead of auto.

After this, and restarting beryl, I was able to open 300 windows.

---

### Post by Tanker Bob on 2007-06-05
Yep, that will work, but you'll also take a performance hit.  How bad the performance hit matters depends on your card.

---

