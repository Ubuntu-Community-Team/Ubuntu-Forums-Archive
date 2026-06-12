---
title: "Gimpshop"
date: 2006-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rush_898 on 2006-10-23
I am completely stumped on this one.  Anyone have any luck?  I have tried downloading a 64 bit rpm and converting with alien, I have tried a 64 bit .deb I found somewhere I can't find again.  I have tried compiling from source and waiding through a host of dependency issues and still nothing.

[http://www.gimpshop.com/#Download](http://www.gimpshop.com/#Download)


here's the from source document I used:

[http://linux.suramya.com/tutorials/Install_GIMPShop/](http://linux.suramya.com/tutorials/Install_GIMPShop/)

I don't know, I'm still a tenderfoot at this linux thing, but I really want to get this gimpshop conversion working as I'm used to photoshop.  Help?

---

### Post by rocknrolf77 on 2006-10-23
Tried this several times before. It's a pain in the neck. Hopefully someone will come up with a more simple solution or do the "dirty work".:)

---

### Post by kuja on 2006-10-24
I did this once before without issue. I think what I did was just doing it from source. First run sudo apt-get build-dep gimp, then download the gimpshop source, extract it, cd into the directory, then run ./configure && make && sudo make install

---

