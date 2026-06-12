---
title: "Could be nit picking here..."
date: 2005-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by UnderRAPS on 2005-12-07
I had some problems with my video resolution (lack of available settings) and tried some things to fix it (didn't work) so just decided to reinstall on top of what was there before. Now I have 3 icons on my desktop sda1, sda5, and sda6. They were not there before during the initial Ubuntu install. I know what they are but want to know if I can hide them or move them to another folder since I don't like icons on the desktop.

Sorry for the novel but I am new to this. :confused:

---

### Post by BoyOfDestiny on 2005-12-07
[QUOTE=UnderRAPS]I had some problems with my video resolution (lack of available settings) and tried some things to fix it (didn't work) so just decided to reinstall on top of what was there before. Now I have 3 icons on my desktop sda1, sda5, and sda6. They were not there before during the initial Ubuntu install. I know what they are but want to know if I can hide them or move them to another folder since I don't like icons on the desktop.

Sorry for the novel but I am new to this. :confused:[/QUOTE]

You can either edit your fstab

sudo gedit /etc/fstab

or 

if you don't like anything to show up on the desktop (i.e. when you plug a usb stick)
You can go to Applications -> System Tools -> Configuration Editor
Then in the editor go apps-> nautilus -> desktop

Uncheck volumes visible. You should still be able to visit them easily from the Places menu.

---

### Post by UnderRAPS on 2005-12-08
OOo!! Thank you BoyOfDestiny for your help :)

---

