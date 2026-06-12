---
title: "Unexpected random logouts"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by rmfought on 2007-04-27
I've noticed this several times since I installed Feisty AMD64 on my Acer Ferrari 4005 - I will be doing some random task and the screen will flicker black momentarily, and then I am presented with the login screen.  Any apps I had open are gone - it's as if I had logged out normally, and I can log right back in.  Anyone else experienced anything like this?

---

### Post by kuja on 2007-04-29
The X server is probably crashing. Unstable video driver perhaps?

---

### Post by rmfought on 2007-04-30
I changed from the "ati"  driver the to proprietary fglrx driver and it hasn't happened again - so I suspect you are correct.

---

### Post by fatalbert on 2007-04-30
How did you do that? I coming across the same thing in Dapper 6.06.

Thanks

---

### Post by rmfought on 2007-04-30
I used the restricted drivers manager in Feisty.

---

### Post by ronocdh on 2007-04-30
> **fatalbert said:**
> How did you do that? I coming across the same thing in Dapper 6.06.

Thanks
A handy method for this is the command
```
sudo dpkg-reconfigure xserver-xorg
```
You can manually choose which drivers to use and also add or remove resolution options.

---

### Post by univremonster on 2007-08-16
Mine has started to do this recently as well.  I am using the restricted driver and have been for some time.  I'd say this happens about every 2 to 3 days.  Any ideas?

---

