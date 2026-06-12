---
title: "permision denied(newbie)"
date: 2008-05-08
forum: x86 64-bit Users
---

### Post by venix on 2008-05-08
ok i am using ubuntu 8.04  x86 64-bit like 2 days i realy love it but i have some problems since i am complete newbie to ubuntu when i am trying to copy paste the flash player when i am trying to copy paste the "libflashplayer.so" and "flashplayer-installer" at /usr/lib/mozilla the system says error :permision denied 
looks like i have no permision to copy files on /usr/******
i have the same problem when i am trying to install the ut2004 with the linux installer ...
does anybody know how i can get the permision to copy files ?

---

### Post by Half-Left on 2008-05-08
Run the installer as sudo, ```
sudo sh myut2004installer.sh
```.

You shouldn't need to to do that for flash player, a dialog will come up asking you which flash to use and do it all for you, just be on a flash page and refresh.

You can copy files either by terminal, ```
sudo cp myfilename /usr/lib
``` or run ```
sudo nautilus --no-desktop
``` and use the filemanager, but be careful when doing this since you can delete anything.

---

### Post by venix on 2008-05-08
thanks thanks thanks you :guitar: everythink works gr8 :)!!!!

+thanks for your profile XD

---

