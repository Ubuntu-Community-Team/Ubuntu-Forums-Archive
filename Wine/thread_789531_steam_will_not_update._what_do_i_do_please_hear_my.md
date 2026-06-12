---
title: "steam will not update. what do i do? please hear my cries!"
date: 2008-05-10
forum: Wine
---

### Post by swankyfb on 2008-05-10
i have just installed steam on hardy heron 8.04, and after the installation, if i launch steam, a green window will appear saying that steam is checking for updates. even if you leave your room for 3 hours and come back, that  same window will be there and steam will still be looking for an update. I know i have a good enough internet connection, and i know i do not need to open any ports, if i could run it on my old 7.10 machine.

what do you think my issue is? 

thank you for taking your time in reading my post

-Swanky farm boy

---

### Post by ubu-for on 2008-10-15
Today I have the [same problem again](http://ubuntuforums.org/showthread.php?t=667009) with Wine 1.0 for Feisty Fawn and Win XP mode.

These Steam updates are making me crazy! Any ideas?

---

### Post by Gcentrex on 2008-10-15
Try this open your steam folder and delete the file ClientRegistry.blob, when I have issues that's the first thing to go then it mostly works after that if it seems to get stuck during an update shutdown steam even if you have to use wineserver -k then follow that up with wineboot and try again.

---

### Post by ubu-for on 2008-10-16
Thanks Gcentrex for your reply but I could solve it by using the Vista mode for the steam.exe in winecfg.

---

