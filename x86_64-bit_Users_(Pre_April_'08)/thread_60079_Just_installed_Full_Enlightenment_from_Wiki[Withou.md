---
title: "Just installed Full Enlightenment from Wiki[Without Name]... now what?"
date: 2005-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by ROUBOS on 2005-08-26
Hi, 
I just installed Full Enlightnement from Wiki[without name]..
Isn't it the desktop theme look ???

How do I activate it to use it???

---

### Post by Tamir on 2005-08-26
[QUOTE=ROUBOS]Hi, 
I just installed Full Enlightnement from Wiki[without name]..
Isn't it the desktop theme look ???

How do I activate it to use it???[/QUOTE]
 It is a window manager, choose it from gdm/kdm/entrance etc.

---

### Post by ROUBOS on 2005-08-26
gdm entrance???? sorry noob here

---

### Post by Tamir on 2005-08-26
[QUOTE=ROUBOS]gdm entrance???? sorry noob here[/QUOTE]
 :) When you start x, you see a programe there you can enter your user/pass and choose a desktop. there, choose enlightenment 0.17.

---

### Post by ROUBOS on 2005-08-26
it's not listed under there

---

### Post by DJ_Max on 2005-08-26
If you have the correct enlightenment.desktop file in your /usr/local/xsessions (I think thats the directory, search for gnome.desktop on your computer). You will have to restart GDM.

---

### Post by ROUBOS on 2005-08-26
Sorry, noob here.
I installed it from "Wiki [Without Name]".
Rebooted the system, and on the logon screen where you choose a sesion, It's not listed

I located  gnome.desktop in /usr/share/xsessions

what do i do??

---

### Post by DJ_Max on 2005-08-26
[QUOTE=ROUBOS]Sorry, noob here.
I installed it from "Wiki [Without Name]".
Rebooted the system, and on the logon screen where you choose a sesion, It's not listed

I located  gnome.desktop in /usr/share/xsessions

what do i do??[/QUOTE]
 Could you link me to the article, as I have no idea what "Wiki [Without Name]" means.

I'm at a family members house, and he doesn't use Linux.  :???: I would make a file called *enlightenment.desktop* in that directory.That gnome.desktop file is pretty self-explanatory. You will need a few of the variables. Most importantly, *Exec*. You need to know the path/to/enlightenment/bin.

---

### Post by ROUBOS on 2005-08-26
link: [http://tamir.nooms.de/wiki/doku.php](http://tamir.nooms.de/wiki/doku.php)

---

### Post by DJ_Max on 2005-08-26
[QUOTE=ROUBOS]link: [http://tamir.nooms.de/wiki/doku.php](http://tamir.nooms.de/wiki/doku.php)[/QUOTE]
 Ahh, I thought maybe you installed from source. Whoever made that package, probably didn't have support for GDM. So following the instructions I provided should do that trick,

---

### Post by Tamir on 2005-08-26
[QUOTE=DJ_Max]Ahh, I thought maybe you installed from source. Whoever made that package, probably didn't have support for GDM. So following the instructions I provided should do that trick,[/QUOTE]
 He did. (it's me) :), it is working for me, and for others. try to install these packages:
[list]
[*]libedb1-dev
[*]libedb1
[/list]
by:
```
apt-get install libedb1-dev libedb1
```
if it doesn't work, close from console GDM by:
```
/etc/init.d/gdm stop
```
then run from console:
```
enlightenment
```
and tell if you have errors.

---

### Post by DJ_Max on 2005-08-26
[QUOTE=Tamir]He did. (it's me) :), it is working for me, and for others. try to install these packages:
[list]
[*]libedb1-dev
[*]libedb1
[/list]
by:
```
apt-get install libedb1-dev libedb1
```
if it doesn't work, close from console GDM by:
```
/etc/init.d/gdm stop
```
then run from console:
```
enlightenment
```
and tell if you have errors.[/QUOTE]
 Ahh, ok. Didn't know that you made AMD64 packages.

BTW, nice contribution to Ubuntu. I'm building a AMD64 box soon, and debating wheither or not to use Ubuntu. If things like these appear, I may have to.

---

### Post by ROUBOS on 2005-08-26
well guys,
I did everything and it worked fine. Installing at least.
Then I logged out. And then tried to log in Enlightenment. So  I select it from the session list, and log in.
I get a popup error message something about my last login being only for 10 seconds..... something like that.

I will write everything down. and post it tomorrow... it's sleep time for me....

Thanks for all your help.. it's been great..

Ubuntu Linux and especialy the work and support from the community.... 

TOP STUFF !!! :grin:

---

