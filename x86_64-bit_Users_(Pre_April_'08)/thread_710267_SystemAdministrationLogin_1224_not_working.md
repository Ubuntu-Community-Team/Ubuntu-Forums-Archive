---
title: "System/Administration/Login 12/24 not working"
date: 2008-02-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lukasz Tarkowski on 2008-02-28
Dear Support
I would like to know how I can change the time to 12 hr in GDM Login Window
I have tried System/Administration/Login Window and to 12 hr and it didn't work :(
By the way the 12 hr time format pls as well :)

---

### Post by Yellow Pasque on 2008-02-28
Try this:
```
sudo gedit /etc/gdm/gdm.conf
```
On Line 495:
> # Always use 24 hour clock no matter what the locale.
#Use24Clock=auto
--->
> # Always use 24 hour clock no matter what the locale.
Use24Clock=false

---

### Post by Lukasz Tarkowski on 2008-02-28
Hey Sup Temüjin
I changed it like you said I wait till like 1:00 pm and see how it goes :)
Thank You Temüjin :)

---

### Post by Lukasz Tarkowski on 2008-02-28
I have tried Use24Clock=false
It didn't work :(
Im sure I did the correct sudo gedit gdm thing :)

---

