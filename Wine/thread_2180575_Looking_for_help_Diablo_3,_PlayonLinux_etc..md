---
title: "Looking for help Diablo 3, PlayonLinux etc."
date: 2013-10-13
forum: Wine
---

### Post by c6coder on 2013-10-13
I just switched over to Ubuntu from another distro I had all my games working over there some hiccups and problems but for the most part they worked and were enjoyable. The last time I used Ubuntu was before the Unity switch over so I think ver 10 or something but anyways I wanto come back to my trustworthy home ubuntu I have a few questions and issues.

First I will start out with my specs:
[B]OS: Ubuntu 12.04 (Gnome Environment)
GFX: NVIDIA GeForce GTX 660 TI (NVIDIA accelerated graphics driver version: 319)[/B]

Now back before this hole craze of "install playonlinux and just install ur game and it magically works" I had to follow threads/tuts on what version of wine to run with each game, what libraries to install etc etc. For some reason I can't find those threads that I followed to get my games running properly so I wen't and did what every body said to do install the game through pol. To my not so suprise diablo 3 was just stuck at "checking for updates" then after some tweaking "updating agent" then more tweaking "windows requires secondary login" I now have diablo 3 working with the following:
[B]Wine ver: 1.7.4, 1.5.26
Librarie overrides: d3dx9_36, msvcr100, openal32[/B]
Diablo 3 is a bit laggy and has no sound, I also noticed is system moniter I'm only using 1.5gb ram max out of my 8.

If anyone could help out with that it would be much appreciated!

Now the next game I'm trying to get running is Path of Exile and I found my old thread I followed and the game updated through the launcher fine but once it launched I got a black screen with an error:
[http://pastebin.com/pwJeZzWM](http://pastebin.com/pwJeZzWM)

If anyone knows of a way I can search the internet easier on how to get these games working properly on linux/ubuntu lmk all I'm finding is "get pol and install game" which does not work for my situation at all, or any things you have tried yourself etc etc lmk thanks and happy gaming all.

---

### Post by martialartist81 on 2013-10-14
How does "get pol and install game" not work for your situation?

Here's the wall-of-text for the Wine APPDB: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953)

Here's PoL supported list (just ctrl-f for "Diablo 3"): [http://www.playonlinux.com/en/supported_apps-1-0.html](http://www.playonlinux.com/en/supported_apps-1-0.html)

It's really quite simple: install Wine, download and install PoL, then open up PoL, search for said game (Diablo 3 in this instance) and install using the predefined scripts, etc.  Just follow the directions.  Makes it quite easy and simple.  And since you say you're having issues with it, just search around the PlayonLinux forums, look under the game information, post to Battle.net, etc.  Not going to tell you how to use Google, c6, that seems a little silly.

Edit: Re-reading your post, I see there you tried PoL, ran into issues and it isn't/didn't work.  Seriously, post PoL issues to the PoL forums as well as here.

---

### Post by c6coder on 2013-10-14
Thanks for the reply martialartist, haven't posted on the other forums yet I will give it a try. Installing through PoL just adds wine gecko it does not add the required configuration to run the games. Everything has switched over to PoL now and the only thing I can find online or turn up is "run pol install game".

I also have searched and can't bring anything up but if I already have the full game and files is there a way using PoL to auto config for that game or is the only option installing the game again through PoL?

---

### Post by martialartist81 on 2013-10-15
Alright... so I have to admit there's some serious guessing going on right now (from me) because I don't own Diablo 3; but bear with me:

- Open PoL
- Install Game (pick Diablo 3)
- Allow it to create a new Virtual Disk/et cetera.
- Log into Battle.net? and download the installer? (guessing)
- Run the installer within the PoL/WINE instance you've created
- the idea is that the PoL instance will have everything preconfigured for you since that's really what PoL does.

You could.. if you have the ability, install the game to your Windows partition, or hell, even a WinXP Virtual Machine if you've got it, then copy that game installation over to the PoL instance, as mentioned in this link: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953](http://appdb.winehq.org/objectManager.php?sClass=version&iId=25953) (just keep in mind that's WINE-based AppDB information, and won't be super helpful to your PoL instance).

Here's a pretty darn good YouTube tutorial (using Linux Mint, however, they install using PoL, so it'll apply to Ubuntu!): [http://youtu.be/fY-7sOkLj9U](http://youtu.be/fY-7sOkLj9U)

Give it a whirl using the video's tutorial.  If you are still having issues, start posting to the PoL forums as well as here.  The PoL folks tend to be pretty awesome (and the Ubuntuforums folks are even more so).

---

### Post by snafu006 on 2013-10-15
Ok now i have to get on this you are making someting so ez to install hard. Why cant you install Diablo 3 ? Use the Beta installer from Battlenet and if gekgo fails just keep go skip it you dont need it.

---

### Post by Toz on 2013-10-15
*Moved to the **Wine** subforum.*

---

