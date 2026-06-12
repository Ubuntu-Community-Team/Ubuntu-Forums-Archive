---
title: "Total Annihilation wont work on wine!"
date: 2007-08-27
forum: Wine
---

### Post by Psyco_Chipmunk on 2007-08-27
I try to install it from the disk bye opening the setup.exe file with wine then the thing comes up saying if i want to install.  I click the install thing and it starts to install, but when it gets to the end, it says "Install Failed! Unable to find readme.txt."

Whats wrong?

---

### Post by Quicky on 2007-08-31
I have exactly the same problem. Not much help, but at least you know it's not just you.

---

### Post by cogadh on 2007-08-31
This may be one of those rare occasions when you need to cd to the install disk before running the setup from the terminal:
```
cd /media/cdrom0
wine setup.exe
```

---

### Post by may88 on 2008-08-03
Hi, just played TA under ubuntu 8.04.
I did not install it from scratch under wine but had a clean install on a windows box which I mounted and run directly from the mount.

I'd followed the TA Universe FAQ to build the perfect TA install.  I have OTA,CC & BT so installed these and then patched to 3.1c, 500 unit patch and then no-cd patch.

Still I had a few issues.  I had to run with wine totala.exe -d
this starts a 800x600 frameless window - at this res there is a problem with the mouse. The pointer is displayed lower than where the click happens.  Knowning this it is then possible to change the visuals to match your screen native resolution and then when you actually play the mouse is fine.  Only tried with Single player skirmish.

---

