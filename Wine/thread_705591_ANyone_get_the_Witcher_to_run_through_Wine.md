---
title: "ANyone get the Witcher to run through Wine?"
date: 2008-02-23
forum: Wine
---

### Post by Shadowmeph on 2008-02-23
I am just wondering if anyone has gotten The Witcher to run properly on wine I have installed the game using win but when I try to launch it through  applications/wine/programs/The Witcher I see the Witcher game launcher on the bottom task bar but nothing happens

---

### Post by Bateluer on 2008-03-27
Did anyone have any luck with this? I have the same issue. 

I attempted to run the game directly through the system/witcher.exe, but the game fails, stating that I don't have root privileges. 

A little digging revealed that it was caused by TAGES. Apparently when you attempt to start the game, it attempts to install the TAGES drivers, which naturally fails under linux. 

I'm running wine .9.58 under Ubuntu 7.10.

Edit - I've also patched The Witcher to 1.2a.

---

### Post by Existance0 on 2008-07-21
I'm also having this problem I saw that the person above me was having permission problems so I figured I would run it under sudo but i get this error from wine...

> wine: /home/arie/.wine is not owned by you

---

### Post by jasonara on 2008-11-16
Hello guyz,
I had the same problem on launching World of Warcraft and after a forum trollin that I did I came to a solution which is : 
Try to launch through terminal..1st) you got to go to the directory that the launcher is installed.  f.e in my wine was sth like that 
cd '.wine/drive_c/World of Warcraft'
2nd) and then simply run the launcher like that :
wine wow.exe

Please let me know if I helped you at all cause I would like to install and play the witcher on ubuntu

---

### Post by mrgnash on 2008-12-04
I got it to launch after putting the Direct3D dll file, and a noDVD .exe in the system/ folder of the game directory. However, there is a major graphical bug that makes the game unplayable for me, and which no workaround appears to be available :(

---

