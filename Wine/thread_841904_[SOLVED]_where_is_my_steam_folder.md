---
title: "[SOLVED] where is my steam folder?"
date: 2008-06-26
forum: Wine
---

### Post by Phyrax on 2008-06-26
I'm new to wine and Ubuntu.

i installed wine and steam through playonlinux, i wanted to copy my data from my other partition (vista) to Ubuntu instead of dl all the games again. but i can't find where the steam folder is. i searched the c drive and then under program files but it's not there.

just wondering where it installed it to, and where to put the data of my steam games.

thanks,
Phyrax

---

### Post by cogadh on 2008-06-28
By default, Steam is installed in C:\Program Files\Steam on Windows. If it isn't found there when you look for it, then I don't know where you might have installed it.

As for where to put the Steam files once you find them, they go in /home/<username>/.wine/drive_c/Program Files/Steam, assumning that you installed Steam in its default location and PlayOnLinuux doesn't do anything funny with where Wine puts everything. Note that the ".wine" directory is a hidden directory, so you will have to show hidden files before you can see it. Also, after copying the Steam files, you will need to delete the ClientRegistry.blob file from the Steam directory, then launch Steam to build a new one, otherwise none of your games will work.

---

### Post by Phyrax on 2008-06-28
i did find it, thanks for your help.

it was in /home/tim/.PlayOnLinux/wineprefix/Steam

---

### Post by Derathor on 2011-02-26
Thanks a lot! :P

---

