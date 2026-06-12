---
title: "lots of problems with world of warcraft :("
date: 2007-12-10
forum: Wine
---

### Post by tysonh on 2007-12-10
I'm using wine 0.9.4.6.  The install of WoW went okay it just took forever to complete.  If i use oss sound in wine the sound skips like crazy and crashes the game.  but then the sound is still playing in the background without wine or wow.exe running.

If I choose alsa nothing works.  I fills up the bar on the load screen but goes no further.

I got in game yesterday after I completed the install.  I had really low fps lower than with vista I couldn't believe it.

I have a AMD socket A 2800 cpu and about 2 gigs of pc 2700.  I'm really a ubuntu novice and I know next to nothing about wine so any tips would be awesome.

thanks in advance :)

---

### Post by LauraSakura on 2007-12-10
You may have to load the game with 
wine wow.exe -nosound
and then when the game starts try either checking or unchecking Hardware Acelleration in the sound menu to the opposite of what you have now then restart without -nosound and see if it works any better.

Also, if possible start WoW from the console and then post here what the output is

---

### Post by tysonh on 2007-12-11
I tried starting wow from the command line and got this:

***@***-****:~$ wine wow.exe
wine: could not load L"c:\\windows\\system32\\wow.exe": Module not found

for some reason it looked in system32, I tried typing out the location but that didn't work either.

---

