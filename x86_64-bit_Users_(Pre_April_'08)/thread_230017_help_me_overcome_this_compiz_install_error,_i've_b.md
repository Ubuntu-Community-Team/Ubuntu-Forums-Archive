---
title: "help me overcome this compiz install error, i've been through 3 reinstalls already!!"
date: 2006-08-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Vlatko on 2006-08-05
i followed this guide that worked a number of times already and now it just doesn't!!!

[http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D](http://tiddlyspot.com/ubuntu/index.html#%5B%5BInstalling%20XGL%2BCompiz%20(64bit)%20(Nvidia)%5D%5D)

after ```
sudo apt-get update
```, ```
sudo apt-get upgrade
``` and editing ```
sudo gedit /etc/gdm/gdm.conf-custom
``` i run this command ```
sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
``` to install all the compiz eyecandy but i get a damn dependency error i can't seem to overcome. i reinstalled my system 3 times already!!

here's the error i get:
```
vlatko@vlatko-desktop:~$ sudo apt-get install xserver-xgl compiz-gnome cgwd gcompizthemer gcompizthemer-themes
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cgwd: Conflicts: gcompizthemer
E: Broken packages
vlatko@vlatko-desktop:~$

```

someone please help!

---

### Post by _simon_ on 2006-08-05
try it without gcompizthemer. The new cgwd has the themer built in... hence the conflict.

---

### Post by Vlatko on 2006-08-05
> **_simon_ said:**
> try it without gcompizthemer. The new cgwd has the themer built in... hence the conflict.
to be honest the troubles started yesterday. i ran a update of the system and the update manager removed gcompiz themer and installed the cgwd themer. i thought that was something messed up so i re-installed the system. are you telling me that was normal? i need to use the cgwd themer, not the compiz one anymore? if so, i'm gonna shoot myself... what's the difference between the 2 anyway? newb here..

---

### Post by _simon_ on 2006-08-05
Yeah that was normal!

I can't tell you why things have changed I'm afraid as i'm not sure myself.

There is however a compiz forum... [http://www.compiz.net/](http://www.compiz.net/)

Oh and don't try and install gcompizthemer-themes either - that won't work.

I think the one you will want is cgwd-themes

---

### Post by Vlatko on 2006-08-05
oh man, oh man, oh man...i had a perfectly good system and i blew it!!! aaaaaah!! why couldn't they have made a notice about it or something?? unbeliavable!!

thanks anyway man.

---

### Post by _simon_ on 2006-08-05
If you're ever not sure about what the update manager wants to install then press cancel and post asking ;)

or post asking afterwards rather than re-installing!

---

### Post by Vlatko on 2006-08-05
yeah, i guess that's the better way. i can't help it so far, from personal experience, it's better to start from scratch than to try and fix something. :D

since you're here already, i have some more compiz install problems. after editing this file with this command:
```
sudo gedit /etc/gdm/gdm.conf-custom
```
and adding this at the bottom:
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```
and following all the other steps and the reboot, when the pc boots again x won't start. i have to re-edit that file and remove ```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true
```

then i save the file and reboot and ubuntu starts normallly. would you know what has to be changed to make it work?

thanks!

---

