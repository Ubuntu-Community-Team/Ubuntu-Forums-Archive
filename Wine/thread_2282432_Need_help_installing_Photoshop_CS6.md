---
title: "Need help installing Photoshop CS6"
date: 2015-06-14
forum: Wine
---

### Post by dadus33 on 2015-06-14
Hi everyone!
I'm new to those forums and to linux/ubuntu. I want to install Adobe Photoshop CS6 on my ubuntu machine but apparently I can only do that using wine. I tried to just double-click set-up.exe and I got a pop-up saying 'Initializing installer' and a loading bar, but at about 80% I got a message saying 'Adobe application manager is needed to solve this problem. However, it is missing or damaged.' and a download link, along with a button to download adobe application manager. I have previously installed PS on windows and never got this message, so I though it might be because the installer needs to be run as admin. I searched for how to accomplish this with wine, and I found out I have to set the widows version wine simulates to windows 98. However, that didn't solve my problem as wine requires windows XP SP 2 or higher to install. I even tried this guy's tutorial here ([http://askubuntu.com/questions/530110/how-can-i-install-photoshop-cs6-on-ubuntu-14-04](http://askubuntu.com/questions/530110/how-can-i-install-photoshop-cs6-on-ubuntu-14-04)) but after pulling the winetricks dependencies I got this message: wine cmd.exe /c echo '%ProgramFiles%' returned empty string and I was still unable to install photoshop. 
I need it really quick, so please help me!

PS:
Running Ubuntu 15.04 if that helps.

---

### Post by leunam12 on 2015-06-15
Try deleting your .wine folder and create a 32bit bottle```
rm -r ~/.wine
mkdir ~/.wine
WINEARCH=win32 WINEPREFIX=~/.wine winecfg
```
Then install the libraries again and try to install. 
Keep in mind that all your other wine software is going to disappear if you do this and you will have to re-install them.

You may also try playonlinux, it makes things easier.

---

### Post by dadus33 on 2015-06-15
> **leunam12 said:**
> Try deleting your .wine folder and create a 32bit bottle```
rm -r ~/.wine
mkdir ~/.wine
WINEARCH=win32 WINEPREFIX=~/.wine winecfg
```
Then install the libraries again and try to install. 
Keep in mind that all your other wine software is going to disappear if you do this and you will have to re-install them.

You may also try playonlinux, it makes things easier.
Thanks for your reply!
Yesterday, I tried using PlayOnLinux, and got it working! Thank you anyways!

---

### Post by leunam12 on 2015-06-15
You are welcome, glad you've got it working.
Photoshop rocks!!

---

### Post by trinaldi on 2015-06-15
Thanks for the instructions, I was just about to start Googling it.

---

### Post by Matejko on 2015-06-19
> **leunam12 said:**
> You may also try playonlinux, it makes things easier.

Never heard about this. Is playonlinux better and easier alternative than Wine?

---

### Post by flaymond on 2015-06-19
I better say 'Windows is better and easier for Windows applications'. Windows application might not run on Linux pretty well like in Windows. However, I feel that playonlinux is better than WINE (especially for non supported windows application that cannot run ***by WINE***) ***based on experiences***. I'm using GIMP as alternative for Photoshop on Linux, and might be vice versa if I'm on Windows. Thank you. Cheers! ;)

---

### Post by leunam12 on 2015-06-19
PlayonLinux is based on WINE, but it makes the installation (and running as well) of a lot of software easier because it automates the installation and also install libraries and stuff that you need to run those programs (The ones that are supported) and it does it automatically.

[https://www.playonlinux.com/en/](https://www.playonlinux.com/en/)

---

### Post by Matejko on 2015-06-22
OK I should try. I see there scripts for Photoshop, but probably Premiere or After Effects wouldn't be supported. Have anyone tried it before?

---

### Post by Matejko on 2015-07-22
I tried it. There is a problem with my RAM - I got 16gb, but Photoshop (via playonlinux) thinks that I have only 4gb. How to fix it?

---

