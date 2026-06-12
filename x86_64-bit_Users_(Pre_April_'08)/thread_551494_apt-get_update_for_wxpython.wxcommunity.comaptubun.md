---
title: "apt-get update for wxpython.wxcommunity.com/apt/ubuntu/feisty64/ ?"
date: 2007-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by ulefr01 on 2007-09-15
sudo apt-get update gives me : 
.....
Genegeerd [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Translation-nl  
Genegeerd [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Release
Genegeerd [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Packages
Genegeerd [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Sources
Fout [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Packages
  404 Not Found
Fout [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Sources
  404 Not Found
199B opgehaald in 2s (81B/s)
Ophalen van [http://wxpython.wxcommunity.com/apt/ubuntu/feisty64/Packages.gz](http://wxpython.wxcommunity.com/apt/ubuntu/feisty64/Packages.gz) 404 
Not Found is mislukt
Ophalen van [http://wxpython.wxcommunity.com/apt/ubuntu/feisty64/Sources.gz](http://wxpython.wxcommunity.com/apt/ubuntu/feisty64/Sources.gz) 404 N
ot Found is mislukt
Pakketlijsten worden ingelezen... Klaar
E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er 
zijn oudere versies van gebruikt.
.
Solution ?

---

### Post by Kilz on 2007-09-15
> **ulefr01 said:**
> sudo apt-get update gives me : 
.....
Genegeerd [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Translation-nl  
Genegeerd [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Release
Genegeerd [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Packages
Genegeerd [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Sources
Fout [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Packages
  404 Not Found
Fout [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Sources
  404 Not Found
199B opgehaald in 2s (81B/s)
Ophalen van [http://wxpython.wxcommunity.com/apt/ubuntu/feisty64/Packages.gz](http://wxpython.wxcommunity.com/apt/ubuntu/feisty64/Packages.gz) 404 
Not Found is mislukt
Ophalen van [http://wxpython.wxcommunity.com/apt/ubuntu/feisty64/Sources.gz](http://wxpython.wxcommunity.com/apt/ubuntu/feisty64/Sources.gz) 404 N
ot Found is mislukt
Pakketlijsten worden ingelezen... Klaar
E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er 
zijn oudere versies van gebruikt.
.
Solution ?

Go to [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com) and ask why their repository doesnt work, or what the settings for it are?

---

### Post by ulefr01 on 2007-09-15
> **Kilz said:**
> Go to [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com) and ask why their repository doesnt work, or what the settings for it are?

How ? Is there an email id that i can use ?

---

### Post by John.Michael.Kane on 2007-09-15
This might be of some help.

```
gksudo gedit /etc/apt/sources.list
```

Add:
```
deb http://apt.wxwidgets.org feisty-wx main
```

Add the key for apt.wxwidgets.org .
```
wget http://apt.wxwidgets.org/key.asc

sudo apt-key add key.asc
```

Update your sources.list 
```
sudo apt-get update

sudo apt-get dist-upgrade
```

install wxWidgets

---

### Post by ulefr01 on 2007-09-16
thank you

---

