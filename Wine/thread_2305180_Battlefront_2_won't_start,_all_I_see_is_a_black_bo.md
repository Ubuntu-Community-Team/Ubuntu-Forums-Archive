---
title: "Battlefront 2 won't start, all I see is a black box."
date: 2015-12-03
forum: Wine
---

### Post by Jared_K on 2015-12-03
**Note: I have the Steam version of Battlefront 2, not the disc version**

Hello! My problem is when I open Steam and play Battlefront 2 (I use Wine 1.6.2 to run Steam), I get a black box in the middle of my screen, a 800x600 black box (picture here: [http://imgur.com/DIGdANm](http://imgur.com/DIGdANm)). If I run it for the first time after I just install Battlefront 2 the box stays for around 12-20 seconds, I can't move or see my mouse, and then the box disappears and so does the Battlefront 2 tab, and when the box disappears I can see and move my mouse again. I check the Task Manager after it closes and I don't see anything Battlefront 2 related. After the first run of the new installation, any other times I try to run it it takes about 5 seconds for the black box to disappear. Does anyone know what could be wrong? Any help is appreciated :D

---

### Post by MikeCyber on 2015-12-04
Run it in a terminal command shell and copy the output here, else we only could guess. Or ask in the wine forum.

---

### Post by Jared_K on 2015-12-04
When I try to run the Battlefront2II.exe in c:/Program_Files/Steam/steamapps/common/Star_Wars_Battlefront_II/GameData/ it just runs Battlefront through steam an I still get the black box :/

---

### Post by howefield on 2015-12-04
Thread moved to the "*Wine*" forum.

---

### Post by MikeCyber on 2015-12-05
again open a terminal and paste the output. change directory to your app and execute something alike:
cd /home/yourname/win*app
wine my.exe

PS: or maybe try playonlinux as this is easier to use

---

### Post by Jared_K on 2015-12-05
I did CD to the directory and use wine to run battlefront, it just ran Steam. How would I use PlayOnLinux, I have PlayOnLinux but I don't know how to use it.

---

### Post by Jared_K on 2015-12-06
I tried using PlayOnLinux but it needs the CD

---

### Post by MikeCyber on 2015-12-06
if you don't paste the terminal output we cannot help as we don't see what's missing/going on.
Installing an app with playonlinux is very easy as it installs all needed stuff. You can select any *.exe. For ex. Photoshop CS6 didn't work in wine but perfectly with playonlinux because I overlooked a needed dll.
Good luck

PS: have a look here:
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=3803](https://appdb.winehq.org/objectManager.php?sClass=application&iId=3803)

---

