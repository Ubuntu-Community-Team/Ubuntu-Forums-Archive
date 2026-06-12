---
title: "[SOLVED] on Gutsy 64 (7.10), i am having problems installing googleearth - GOOGLE EAR"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicolasdiogo on 2008-01-06
hi folks,

i have red other threads on this forum on how to install google earth on gutsy 64 but i am not having any luck.

in order to avoid any problems i have added medibuntu as a repository from where i am installing my google earth from. thus synaptic should have ensured that all dependencies are correct. but that is not the case.

after installing it from synaptic and starting it from the terminal i receive the following message:

Segmentation fault (core dumped)

would any one know might be done to fix this problem? :confused:


Many thanks,

---

### Post by koenbeek on 2008-01-16
I downloaded google earth 4.2 beta from [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

and then did a sudo sh ./GoogleEarth.bin to install it and am having no problems on gutsy amd64

(the first time I installed it without using sudo, and then it crashed for me too)

---

### Post by yuriry on 2008-01-16
I downloaded Google Earth using Synaptic and do not have problems using it, but I'm on 32bit (Centrino Duo)

---

### Post by Yellow Pasque on 2008-01-16
[http://ubuntuforums.org/showthread.php?t=520952&highlight=google](http://ubuntuforums.org/showthread.php?t=520952&highlight=google)

---

### Post by nicolasdiogo on 2008-01-17
thanks,

i will have a go in using the files and post back once i tried it.

---

### Post by fonsi2099 on 2008-01-22
The situation is as follow for me: 

(setup.gtk2:6873): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory
some help to fix that:confused:

1000 thanks
):P

---

### Post by nicolasdiogo on 2008-01-28
yep,

it is working now.
eventhoug i am using a nvidia card this solution has worked.

i have downloaded the libraries and placed into googleearth folder:


sudo mv libGL.so.1 /usr/lib/googleearth
sudo mv libGL.so.1.2 /usr/lib/googleearth

thanks a lot

---

