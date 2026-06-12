---
title: "Need help on lates Nvidia propietary drivers"
date: 2006-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by leftyman on 2006-05-07
Hello:

Can someone tell me (or link a howto) to install the latgest Nvidia propietary
drivers in my amd64 SYSTEM?

thanks in advance

---

### Post by kaffeine on 2006-05-07
```
sudo apt-get install nvidia-kernel-common nvidia-glx
```

this is the easiest and quickest way to install the LATEST Nvidia proprietary drivers (version 8756 currently).

---

### Post by leftyman on 2006-05-07
Installing them this way I get no control panel and games give me errors like this:

Xlib:  extension "GLX" missing on display ":0.0".

Excuse me I am a newbie

thanks

---

### Post by kaffeine on 2006-05-08
check your /etc/X11/xorg.conf for the "Module" Section and see if 

```
Load     "glx" 
```

is commented out. if it is, uncomment it and restart X (Ctrl+Alt+Bkspc). 

Also make sure that Load "GLcore" and Load "DRI" are commented.

---

### Post by kaffeine on 2006-05-08
i forgot to mention - are you talking about the nvidia control panel? (X-server settings) for me they were installed with nvidia-glx so you should be able to access them at Gnome>System Tools>X-server Settings. you can also check if glx is enabled here.

if you do not have this in your menu, you can install it seperately - more details [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") (see in method 1).

---

### Post by leftyman on 2006-05-08
Thank you kaffeine

pepole like you make me want to go on with ubuntu  despite
the difficulties for  a newbie.

I didnt have de load glx option


now I have the control panel and opengl activated (of course with latest drivers)

thanks

---

### Post by trugate on 2006-05-09
[QUOTE=kaffeine] ...uncomment it and restart X (Ctrl+Alt+Bkspc).[/QUOTE]

You don't know how long I've been googling for how to do this.  So many people say 'and simply restart the X server'.  ](*,) 

I'm a WinXP user, trying so very hard to switch atm, aka complete n00b.  Thank you for spelling this out.

---

