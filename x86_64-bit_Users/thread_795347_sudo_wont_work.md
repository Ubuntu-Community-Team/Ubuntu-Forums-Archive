---
title: "sudo wont work"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by j3susxxx on 2008-05-15
hi im tring to instal nvidia-linux-x86-169.12-pkg1.run...i kinda know how to instal it but wen i try to instal it in Ctrl+Atl+f1 it asked me for my USER-desktop login: wish is my usual passwork but after it asked my fo another password wish i guess is the sudo but it wont work ](*,)

thx in advence

---

### Post by Kilz on 2008-05-15
> **j3susxxx said:**
> hi im tring to instal nvidia-linux-x86-169.12-pkg1.run...i kinda know how to instal it but wen i try to instal it in Ctrl+Atl+f1 it asked me for my USER-desktop login: wish is my usual passwork but after it asked my fo another password wish i guess is the sudo but it wont work ](*,)

thx in advence

User-desktop login is your username. The password is the password.

---

### Post by j3susxxx on 2008-05-15
:-\" thx a lot

---

### Post by j3susxxx on 2008-05-15
now to instal the nvidia driver i got to stop x server but i dont know how can anyone help me

sry for those stupid questions but im new to linux

---

### Post by GTengineer on 2008-05-15
> **j3susxxx said:**
> now to instal the nvidia driver i got to stop x server but i dont know how can anyone help me

sry for those stupid questions but im new to linux

I am assuming you are using Gnome

press ALT-CTRL-F1

and then do:
sudo /etc/init.d/gdm stop

Install the drivers and then do:
sudo /etc/init.d/gdm restart

Make sure to select the option to configure xorg when you are installing the drivers.

---

