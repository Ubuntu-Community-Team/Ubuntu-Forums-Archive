---
title: "Anybody use the ActiveX plugin?"
date: 2006-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Doctor J on 2006-11-08
I'm interested in viewing music videos from this site: [http://www.singingfool.com/](http://www.singingfool.com/) .  However, they require an ActiveX plugin.  They give the link for said plugin to use in FireFox 1.5, but installation fails, even in firefox32.  Any Help?

---

### Post by Paul41 on 2006-11-08
You could try to use IE to view that site. This is not ideal because you would have to use IE for that site, but it would probably work. [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

I would also complain to the site owner about making ActiveX a requirement.

---

### Post by Kilz on 2006-11-08
> **Doctor J said:**
> I'm interested in viewing music videos from this site: [http://www.singingfool.com/](http://www.singingfool.com/) .  However, they require an ActiveX plugin.  They give the link for said plugin to use in FireFox 1.5, but installation fails, even in firefox32.  Any Help?

Active x is a security risk. If you want to ignore the risks for the sake of watching video's Here is what you do. This plugin is only for the 1.5.0.* versios of firefox32.
[Download the plugin]("http://www.iol.ie/~locka/mozilla/mozactivex-ff-15.xpi").
place it on your desktop. open a terminal and paste this in.
```
sudo cp -r -p ~/Desktop/mozactivex-ff-15.xpi /usr/local/firefox32/plugins/
```
Restart Firefox and hope and pray that you dont have any exploits used against you.

---

