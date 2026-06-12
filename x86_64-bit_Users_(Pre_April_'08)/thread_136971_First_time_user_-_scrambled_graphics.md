---
title: "First time user - scrambled graphics"
date: 2006-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by elusive_fish on 2006-02-27
Hi all, I have been meaning to try Linux out for a long time now and a IT friend suggested Ubuntu.  I installed the 64 bit version in a dual boot set up and everything seemed to work well... until it tried to load the GUI.

All I get is a horrible scrambled pattern of colours.  I have tried googling this problem, but either can't find anything or im too new to actually know I found the right answer :-k 

Can someone point me in the right direction please!

BTW
I have an NVIDIA 6600GT displaying on a Samsung SyncMaster 712N 17" LCD

---

### Post by Jason_25 on 2006-02-27
This is a very common problem with the older versions of the nv driver.  The 6600 isn't supported by it.  CTRL-alt-f1 will get you to the terminal.  Then type
```

sudo dpkg-reconfigure xserver-xorg

```
and enter your password.  Choose sane options until you get to the driver section.  Instead of nv, choose **vesa**.   Then
```

sudo /etc/init.d/gdm restart

```
 That will get you going until you get into the gui.

---

### Post by elusive_fish on 2006-02-27
Awesome! Thanks for the fast reply - I am now writing to you via Ubuntu :p 

I downloaded the latest NVIDIA drivers... but don't have any idea how to install them.  More help please? :mrgreen:

---

### Post by uniko on 2006-02-27
[Here]("http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia") is a nice howto to install latest nvidia drivers.

---

### Post by towsonu2003 on 2006-03-28
[QUOTE=elusive_fish]
I downloaded the latest NVIDIA drivers...[/QUOTE]
Having stupid ATI as my video card, I'm absolutely jealous of you.

---

### Post by zapcojake on 2006-03-29
you can sudo nano /etc/X11/xorg.conf and scroll down to the line that says driver and change "nv" or what ever is there to "vesa" then press ctrl+o then ctrl+x then startx.  That will change only the driver that gets loaded.

---

