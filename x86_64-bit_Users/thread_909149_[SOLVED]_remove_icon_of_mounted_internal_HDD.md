---
title: "[SOLVED] remove icon of mounted internal HDD"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2008-09-03
Hi,

Some time ago I mounted a internal HDD and linked to a folder. *quite proud of himself*

However on my Desktop, this icon " Media of 1000MB" is hanging around. 

Can anyone help me to remove this icon / item on my desktop??

I know it is possible, I have seen somewere a how to...but cant find it.

Kind regards,

Bloemetjesgordijn

---

### Post by John.Michael.Kane on 2008-09-03
> **Bloemetjesgordijn said:**
> Hi,

Some time ago I mounted a internal HDD and linked to a folder. *quite proud of himself*

However on my Desktop, this icon " Media of 1000MB" is hanging around. 

Can anyone help me to remove this icon / item on my desktop??

I know it is possible, I have seen somewere a how to...but cant find it.

Kind regards,

Bloemetjesgordijn

Note this will prevent all mounted volumes from being visible on the desktop:

Run this from your terminal.
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'
```

To reengage volumes being visible change the value to 'true'.

Hope this helps.

---

### Post by philinux on 2008-09-03
If you'd like a gui to tweak such stuff look here.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Bloemetjesgordijn on 2008-09-05
Thx for the advise

Is there also a way to rename the Media thingy in lets say Download...

Thx

Bloemetjesgordijn

---

