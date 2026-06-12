---
title: "Phantasy Star Online Blue Burst"
date: 2007-11-29
forum: Wine
---

### Post by Shmifty on 2007-11-29
Is there any way to get PSO:BB to work under Wine? I've searched around and I'm unable to figure out why it keeps crashing.

---

### Post by cogadh on 2007-11-29
I believe PSO uses GameGuard, so it will likely never run in Wine. GameGuard installs as a virtual driver in Windows and Windows drivers do not work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3092](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3092)

---

### Post by Burbruee on 2007-12-12
If you play on a private server, their patch disables Gameguard. I've been able to succesfully launch the game title screen, however, that's as far as I van go.
I can't input my account details. On Windows XP/Vista you solve this by installing japanese IME. (Because it's the japanese client) I don't know if there is a way to do this on ubuntu and if it would make it work. 

Anyway, with cedega it is actually possible to type in account details, but the game crashes after you click on "Start Game" :(

So sorry, I have not been able to get in-game with it, but at least got it to start. :)

---

### Post by wjluelf on 2008-01-10
If you install imm32.dll and set it to native with winecfg you'll be able to enter your information.  I'm suffering from a problem that the when you do this it keeps scrolling through the options on the menu even with no buttons pressed.  Even if you get the information in and start the game, it begins loading and then immediately crashes afterward.

Hope this helps.

~W

---

### Post by landeel on 2008-01-29
The imm32.dll trick worked for me.
The cursor scrolling problem is related to joysticks. Just remove any plugged joysticks/joypads before launching the game and it won't happen.
Still the game crashes, but thanks for the info.

---

### Post by landeel on 2008-05-04
I have filled a bug report about the PSOBB crash on wine's bugzilla. It's here: [http://bugs.winehq.org/show_bug.cgi?id=12964](http://bugs.winehq.org/show_bug.cgi?id=12964)
Please check it out. And add any useful information you may have and VOTE. Maybe the devs can get it working for us.

---

