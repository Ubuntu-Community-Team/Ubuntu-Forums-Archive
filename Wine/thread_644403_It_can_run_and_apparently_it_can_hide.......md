---
title: "It can run and apparently it can hide......"
date: 2007-12-18
forum: Wine
---

### Post by Immolatus on 2007-12-18
:confused:This is my first go at wine...I've installed an older win rpg in wine using the sticky instructions in this forum. It launches from applications-->wine-->ect. And it runs.....But here is the problem: I can't see it running "top" shows the ".exe" running and so does the system monitor but I can't see it anywhere. I tried turning off the desktop effects too, no help. any thoughts???:confused:

---

### Post by The Noble on 2007-12-18
try running it under an emulated desktop because it might be starting offscreen.

---

### Post by Immolatus on 2007-12-18
K. Tried that, if the pic uploaded ....here's what it did.

---

### Post by weblordpepe on 2007-12-19
Nice theme!!! What theme are you running on that desktop???
Anyway, run TOEE.EXE from the console. That will output any errors back to the console.

How to run it from the console:
Open a terminal/console by hitting **alt-F2** and typing **gnome-terminal** then hitting enter. That opens a terminal window.
Use **cd** to get to the directory where the EXE is. For example:
**cd /home/username/.wine/drive_c/Program\ Files/toilet**
(Assuming **toilet** is the name of the installation dir and **username** is your login/username)

Then use this to run it:
**wine ToEE.EXE**

---

### Post by Immolatus on 2007-12-19
Ok. tried that.....here's the result. Don't worry I'm not a quitter. I'll figure this out one way or another.

---

### Post by Immolatus on 2007-12-19
Sorry for reposting......the theme is my own spin on the emerald default theme over top of metacity "tenebrific" theme from the art manager. I tried to upload the theme for you but it wont let me "invalid file" something or other.

---

### Post by cogadh on 2007-12-19
Next time, instead of screen shots, just copy/paste the text out of the terminal into the post, it is easier to work with.

The error you got (the "CDROM_DeviceIOControl Unsupported IOCTL.." part) indicates the SecuROM copy protection on the game is not working. What version of Wine are you using? The most current version (0.9.51) has pretty good SecuROM support and most games that use it will work. If you are already using the latest, then you might need to create a symbolic link to your CD-ROM's /dev entry in Wine's dosdevices directory. Click on the "Stuff I've learned about Wine" link in my sig and go to the "Special configuratiion stuff" section, it is explained there.

If that doesn't fix the problem, then you might need to use a cracked executable to run the game. Don't ask where or how to get one, you'll have to figure that out for yourself (the discussion of cracks is against the forum rules).

---

### Post by Immolatus on 2007-12-19
k...so I completely removed the previous version (0.9.46) and downloaded (wine-0.9.51.tar.bz2). How would you suggest I install it?
 extract to /home then 
./configure
make
make install?

---

### Post by cogadh on 2007-12-19
Don't bother with that, use the WineHQ Ubuntu repository and install the precompiled DEB package. Instructions here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Immolatus on 2007-12-19
no dice it did the same thing....i'll take your advice and search elsewhere....thanks

---

### Post by cogadh on 2007-12-19
Did you try setting up the symbolic link after installing 0.9.51 as I suggested? Just having that set up right can make copy protection work.

---

