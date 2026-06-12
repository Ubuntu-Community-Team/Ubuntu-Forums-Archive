---
title: "Installing Iexplore.exe?"
date: 2008-06-03
forum: Wine
---

### Post by videoman1994 on 2008-06-03
How do I install this with wine I am a complete newbie and need a very explanatory guide, and if someone could teach me how to configure wine correctly, all I did was install wine and left it there but now I need it, thanks in advance.

---

### Post by cogadh on 2008-06-03
The first place you should go before using Wine is the [WineHQ website](http://www.winehq.org/) followed closely by Wine's [Application Database](http://appdb.winehq.org/), which would tell you that trying to install Internet Explorer directly in Wine is generally a waste of time:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=25](http://appdb.winehq.org/objectManager.php?sClass=application&iId=25)

If you really need to use IE in Linux, then what you want is [IEs4Linux](http://www.tatanka.com.br/ies4linux/page/Main_Page).

---

### Post by kostkon on 2008-06-03
If you mean you have an application that needs to use IE as a backend, then you'll need to install Wine's replacement for IE (which actually uses the Gecko engine), by opening a terminal and giving:
```
wine iexplore.exe http://www.winehq.org/
```

---

### Post by aysiu on 2008-06-03
Follow these instructions:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

