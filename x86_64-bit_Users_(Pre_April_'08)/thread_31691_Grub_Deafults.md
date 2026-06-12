---
title: "Grub Deafults"
date: 2005-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by rhino_of_stockton on 2005-05-04
How do i set the deafults in grub, i tried chaning the menu.lst file but i have no access (only root has access to the file) and i have tried logging on as root but with no avail. all i want to do is change the deafult boot to be changed from ubuntu to windows as i am not the only user of the computer and the rest of the family dont know how to use linux  :-( , so they need windows and i need to make windows the deafult booter. the distros (linux and windows) are on the same hard drive on separate partitions on HDa.

Many thanks
Rhino_of_stockton

---

### Post by Juergen on 2005-05-04
To know how to do admin-tasks in Ubuntu, you should read this:
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

And if you read this:
[http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions) 
you'll find that, in short, you need to do
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by nad on 2005-05-04
Use the command:  sudo gedit /boot/grub/menu.lst  to edit this file as root. Now you will be able to save changes.

The most persistent way to make an option the default is to put it first in the list, above the automagic section, this way it will not be touched by update-grub.

Second: By changing the 'default' line near the begining of the file to have the parameter 'saved' instead of zero, the current boot selection will be the default upon restart. Just make sure that the option 'savedefault' is included in that operating system boot description.

Third: Changing that 'default' line near the top of the file again to a number, will boot that operating system and often requires a little try and error to find the correct parameter.

---

### Post by rhino_of_stockton on 2005-05-05
thats great i can now get my dad off my back lol :razz: 

Thanks
Rhino_of_stockton

---

