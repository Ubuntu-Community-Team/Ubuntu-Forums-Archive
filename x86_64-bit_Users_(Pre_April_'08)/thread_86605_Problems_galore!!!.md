---
title: "Problems galore!!!"
date: 2005-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Elendil on 2005-11-05
For starters: What kind of system does not detect a PCI express ATI X800 these days?? Well honestly I hate MS but at least I can see SOMETHING in my GUI and do not have to fondle around in a DOS/UNIX console trying to get things to work. I left that kind of OS around 10 years ago. Anyone out there that cannot start the X-Server with an X800 in conjunction with an nForce4 MoBo? Help is appreciated. 

Greetings

Mark
P.S.: I need someone with profound knowledge. Not that typical try this and try that. I tried it all! At least all standard help bits out of all these forums. What I need is a step by step to install ATI drivers out of the console or whatevaaaa....long live Bill Gates!

---

### Post by RAOF on 2005-11-05
You can get some kind of gui-love happening with the vesa driver.  In order to do that, run
```

sudo dpkg-reconfigure xserver-xorg

```
and selecting the "VESA" driver when asked (it will probably default to "ati").  This will (almost certainly) get you a working X server.

As for getting the proprietry ati fglrx drivers working, I don't know how to do that, I've got a nvidia card.  I **do** know that a lot of people have been having troubles.  It seems that that's been fixed, though.  This [howto]("http://ubuntuforums.org/showthread.php?p=408111") seems straightforward.

---

