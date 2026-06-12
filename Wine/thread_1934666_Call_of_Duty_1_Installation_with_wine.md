---
title: "Call of Duty 1 Installation with wine"
date: 2012-03-02
forum: Wine
---

### Post by hurricanedt on 2012-03-02
Hey everyone,

Everyone here is extremely helpful so I figured I would come to you guys for help on this.  I want to install CoD1 on 11.10; however, it is a two disc installation.  I have spent hours upon hours searching forums but nothing I have tried has been successful.  Does anyone have any ideas at all on doing a multi disc installation?

Thank you,

Demetri

On a side note, does anyone have any tips to make ubuntu run faster?  I have an older ex-windows XP computer so sometimes ubuntu runs laggy.

---

### Post by imachavel on 2012-03-02
this is a no go man. I've had this same problem, and have asked questions repeatedly on how to install it, without any good advice. Linux supports opengl, so it should be able to play call of duty 1. Obviously the disk won't work. When you take the files off the disk and put them into a folder, into a directory, you need to make two directories, one for each disk right? Then for the install.exe, you right click properties, and give the executable box a check mark indicating wine will run it as an executable. Then you right click the file, and select to run the install with wine. Starts working, works great, then it asks for second disk, SCREWED!

the problem here is that there is no script written in any of the directories to look in another directory for the second disk. It should be written in c++ with classes. Man, I don't know the answer, if I did, I'd tell you how to write the code, and would have probably written it myself. It sucks, what an awesome game.

You could, download virtualbox ose, configure the settings of vm, install windows xp in a virtual hard drive(call of duty 1 won't work in windows 7 trust me opengl support is horrible), then configure all your usb filters, configure a high amount of vram(I think anything over 100mb of vram should be good), when the OS installs and you have all your drivers installed, etc. from desktop, if the vm capture mode is full screen, go to the top menu, look around in the task menus for guest additions, install them. But trust me, gaming in a vm is a bad idea, I don't know the mouse won't stop acting up. The game loads and plays though, you just can't get anywhere with the mouse looping around retardedly

---

### Post by hurricanedt on 2012-03-02
ooh thats depressing.  that really stinks.  wish there was a way! who knows, maybe some genius will have the code to do it.

---

### Post by hurricanedt on 2012-03-02
please if anyone has any advice at all on how to do this it would be great.

---

### Post by howefield on 2012-03-02
Thread moved to the "*Wine*" forum.

---

