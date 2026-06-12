---
title: "ubuntu 32 bit 12.10 and wine installation"
date: 2013-03-11
forum: Wine
---

### Post by carliewolf08 on 2013-03-11
I'm new to ubuntu, formally windows 8 disgusted and have switched my other computer over to ubuntu only.  The only  thing I want to run on wine is to download DB Weave (and possibly for netflix later).  I'm very confused with the wine install choices.  I tried downloading the microsoft windows compatibility layer (meta-package) from my ubuntu installer software center and it would not install the whole thing.  I'm assuming it was not the wine program?  I see options for a lot of others like wine 1.4 dbg; wine 1.4 common; wine 1.2 and wine 1.3  Was I suppose to install one of these? I have never used a terminal so was hoping this could be done through the install package that comes with ubuntu.  I have read some of the instruction sections but I'm still really confused.  Any help would be appreciated.

---

### Post by Mr. Shannon on 2013-03-11
I would need to see the error it gave you.  Try opening a terminal (ctrl+alt+t) and typing:
```
sudo apt-get install wine
```
and post any error messages here.  Please use [noparse]```
error message
```[/noparse] tags when positing the output to make it more readable.

**EDIT**: As for Netflix, you should use the special Netflix app created by Erich Hoover that uses a custom version of wine.  You can install it using the instructions here ([http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019](http://www.techrepublic.com/blog/opensource/how-to-get-netflix-streaming-on-ubuntu-1210/4019)).

---

