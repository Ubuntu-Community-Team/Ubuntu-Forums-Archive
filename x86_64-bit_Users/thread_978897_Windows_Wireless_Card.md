---
title: "Windows Wireless Card"
date: 2008-11-11
forum: x86 64-bit Users
---

### Post by lampzzz on 2008-11-11
I am currently following a tutorial on how making my wireless work in ubuntu

I had to access this page to get my driver
```
http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/
```

But I don't think the page exists anymore, as it's just blank :(


Can anyone help?

---

### Post by saru411 on 2008-11-11
It would help if you posted your NIC's info. Have you tried system>administration>hardware drivers?

---

### Post by lampzzz on 2008-11-11
Component                  Enabled  Status

Device driver
nvidia_new              marked     Not in use

---

### Post by lampzzz on 2008-11-11
Can anyone help? Sorry for rushing but I really just want this to work..

---

### Post by nikgare on 2008-11-11
What card is it?

---

### Post by lampzzz on 2008-11-11
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by lampzzz on 2008-11-11
Now I've been searching for hours! No luck :S

---

### Post by Yellow Pasque on 2008-11-11
What wireless card do you have?
```
sudo lshw -C network
```

---

### Post by lampzzz on 2008-11-11
BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

---

### Post by lampzzz on 2008-11-11
I think I have found the driver, I will try it I found this

[http://www.versiontracker.com/dyn/moreinfo/win/98294&mode=feedback](http://www.versiontracker.com/dyn/moreinfo/win/98294&mode=feedback)

---

### Post by lampzzz on 2008-11-11
When I try to install it, it says not a valid .inf file

---

### Post by nikgare on 2008-11-12
Because it's an exe file- for windows!

It seems that you'll have to use ndswrapper, this page should help:
[http://ubuntuforums.org/showthread.php?t=742986](http://ubuntuforums.org/showthread.php?t=742986)

---

### Post by BunTai on 2008-11-12
thanks..
now my wireless card used!

---

