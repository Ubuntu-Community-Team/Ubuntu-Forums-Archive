---
title: "instalingl new graphics card, install new OS?"
date: 2007-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Greykrrr on 2007-02-01
Hi

I'm going to be the fortunate owner of an 6200 nvidia card very soon. Fortunate because I currently own a 9600 Radeon card and I am really fed up with ATI issues.

Now with all the fiddling about it requires to install a proprietary driver in Ubuntu in order to a clean switch from ATI to Nvidia is a clean install recommended?

---

### Post by Rui Pais on 2007-02-01
You want to suffer??

You only need nvidia drivers  (from restricted modules or from nvidia site) and change your xorg.conf to nvidia, removing the radeon driver line or any other radeon specific option.

You can do it in 2 steps just change to  nv driver (the free one) ensure thet evrything works, install nvidia property driver, change xorg.conf, load module and restart xserver. Easy :)

---

### Post by Greykrrr on 2007-02-01
Ah that is brilliant! I was hoping for such an answer. I would hate to loose all my configuration settings, so no, I definately don't want to suffer but I do appreciate a smooth and efficient system and if I can have that in a few easy steps so much the better!

That just means more time for programming and drinking coffee :)

---

### Post by Greykrrr on 2007-02-01
.

---

### Post by RAOF on 2007-02-01
In particular, the steps you want to take are:

Before replacing cards:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```and select the "vesa" driver.  That way, when you switch cards, you still get a GUI to come back to.

Switch the cards.

Load up, and run ```
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```
Restart X (by logging out and pressing Ctrl-Alt-Backspace, or by running "sudo /etc/init.d/gdm restart").

You're all done.  Shiny new nVidia drivers.

---

