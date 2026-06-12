---
title: "American Mcgee's Alice and Wine"
date: 2006-06-25
forum: Wine
---

### Post by Footissimo on 2006-06-25
Finally got a game to work near perfect with wine..woohoo!

However, there is still one annoyance.  The game works great and all that, but when I quit, it leaves the desktop with colour (green) splurged all over it.  It's no big deal, but it means I have to spend a minute clicking around so I can see all the desktop again.  I presume this is a Wine thing...is there any settings I can use that will make it quit clean?

Oh and if anyone is wondering how to get this great game to work:

Didn't use the loki installer - it installs but then the game stops when it starts on the first level.  I just installed it on my mini-Windows XP partition, then copied and pasted the whole of the EA Games directory under Program Files and put it in the same place under ~/.wine.  Then just made a little script (named 'alicego'), which went like this:

```
#!/bin/sh

cd ~/.wine/drive_c/Program\ Files/EA\ GAMES/American\ McGee\'s\ Alice/
wine alice.exe
```

and did a:

```
chmod +x alicego
```

..and used that to make a menu entry (with the icon from the loki installer)

---

### Post by bocmaxima on 2006-06-25
I dont have a Windows partition, you think there might be abother way (install it on my GFs comp, then burn to a CD and bring it over, maybe?)

Right now the installer crashes so hard I have to log out.

---

### Post by Footissimo on 2006-06-25
I can't see why not - I've tried the 'sledgehammer' copy/paste method twice now and its worked both times.  Worth persisting with installing it though - have you tried the [Loki](http://www.liflg.org/?catid=6&gameid=75) installer?  It still requires Wine..and it didn't work for me, but...

Which version of Wine are you using?  I am using 9.16, didn't use the version in the ubuntu repos

---

### Post by bocmaxima on 2006-06-25
[QUOTE=Footissimo]I can't see why not - I've tried the 'sledgehammer' copy/paste method twice now and its worked both times.  Worth persisting with installing it though - have you tried the [Loki](http://www.liflg.org/?catid=6&gameid=75) installer?  It still requires Wine..and it didn't work for me, but...

Which version of Wine are you using?  I am using 9.16, didn't use the version in the ubuntu repos[/QUOTE]


Loki installer worked for me for the most part, but the game doesnt run to well, and right after the first scene with the Cheshire cat it kicks me to the main menu...strange.

---

### Post by Footissimo on 2006-06-25
Sounds the same as me when I tried the Loki installer.  Stick a NoCD replacement for alice.exe when you install on Windows and then copy/paste it over.

Remember to adjust your permissions if you copy to CD then to HD again - it'll all go to read only once you paste it.

A (bad) workaround for the green screen thingy is to adjust the settings in-game so that you're playing in a window.  Googling around seems to suggest its a DirectX 'thing'. Ho hum

---

### Post by frenchn00b on 2008-02-08
Is there still a loki installer for this game ?

I d like to play it

---

### Post by cogadh on 2008-02-09
You don't need the Loki installer anymore, you can install the game normally in Wine. Just follow the install/configuration instructions here:
[http://appdb.winehq.org/appview.php?iVersionId=374](http://appdb.winehq.org/appview.php?iVersionId=374)

---

