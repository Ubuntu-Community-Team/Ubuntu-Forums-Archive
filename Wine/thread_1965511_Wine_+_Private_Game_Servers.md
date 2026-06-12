---
title: "Wine + Private Game Servers?"
date: 2012-04-25
forum: Wine
---

### Post by Bluphx on 2012-04-25
Heya I'm playing with wine and got through troubleshooting and installing the game (Lineage 1 old school i know ^^) but normally for private servers you type the IP address at the end of the target line (IE c/program files/ncsoft/lineage.exe "serverIP") but in Wine i can make a desktop shortcut but the target line is **uneditable**... Is there a terminal command to manually launch the exe to connect. Sorry I'm new to ubuntu don't know the terminal commands yet.. lol I keep typing sulu (like from star trek) by mistake ^^

Other than that, is there a hex editor or something, thats i can edit the clients default IP address? (NCSoft shutdown live server so IP goes to nowhere at the moment).

---

### Post by cogadh on 2012-04-26
AFAIK, Lineage does not work in Wine, private server or not. However, if you were to type a terminal command to run it, it should be as simple as:

wine /path/to/lineage.exe "server IP" <-- replace that "/path/to/" with the actual application path (I don't know what it is)

Note that I said "should", I make no guarantee that it will work at all.

BTW - Private servers are a legally questionable area (in most cases) and are not a topic that is normally allowed here. Given that the Lineage official servers are shut down, the mods might not have a problem with it this time, but don't be surprised if this thread gets a lock.

---

### Post by Bluphx on 2012-04-26
Yea I guess, they were legal even when NC had the server up should be fine. Anyways thanks, I'll try it out. If it does work can i build a scipt so i don't have to terminal every connect? Im coming from mac so i'm use to making automator scripts..

---

### Post by Bluphx on 2012-04-26
There's a space in my path "Program Files" and terminal is getting hung on the path. This is what it looks like

$ wine /home/usr/.wine/dosdevices/c:/Program Files/NCSoft/Lineage/Lineage.exe "##.###.##.##"

the response in terminal is..
wine: cannot fine '/home/usr/.wine/dosdevices/c:/program'

tried it with no space but doesn't see the correct path. Open to suggestions ^^

---

### Post by cogadh on 2012-04-26
wine /home/usr/.wine/dosdevices/c:/Program\ Files/NCSoft/Lineage/Lineage.exe "##.###.##.##"

The backslash will allow the terminal to "see" the space.

---

