---
title: "Wine - no cd"
date: 2007-12-10
forum: Wine
---

### Post by ghonz on 2007-12-10
I'm having problems running games under wine.
I have Ubuntu 7.10 on a HP Pavilion TX1138ea.  The games install ok but when I try to play each game says 'error wrong cd inserted'

Anyone got any advice?

---

### Post by cogadh on 2007-12-10
It would help to know what games you are trying to run and what errors (if any) are output to the terminal when you run the game.

It should be noted that Wine does not have complete support for game copy protection schemes. SecuROM works nearly fully and some SafeDisk protected games will work, but otherwise you will likely have to use a "no CD" cracked executable for any games that use other copy protection schemes.

---

### Post by ghonz on 2007-12-10
So far I've tried it with:
Star Wars Jedi Knight II
Star Trek Away Team
Rome Total war

with each game I've installed them from the CD ok, and I get through the introduction movies.  Then when I click to start a new game they say the wrong disc is in and to insert the play disc.

---

### Post by cogadh on 2007-12-10
Don't know about Away Team or Total War, but Jedi Knight 2 works fine without a no-CD crack,  you just need to have Wine configured correctly. First you need to make sure that your CD drive is configured as type "CD-ROM" on the Drives tab in winecfg. The second thing you need to do is create a symbolic link to the drive's /dev entry in Wine's dosdevices directory. Assuming your CD drive is /dev/hdc and your drive is configured as the "D:" drive in Wine, run this in terminal:
```
$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
```
If your CD drive has a different /dev entry or you have it configured as a different drive letter in Wine, modify the line above to match your correct settings.

---

### Post by ghonz on 2007-12-11
I just tried all that with no joy :(
I'm still getting "Error: Game CD not in drive"

---

### Post by cogadh on 2007-12-11
Are you using an original game CD or a *ahem* copy?

---

### Post by ghonz on 2007-12-11
originals :)

---

### Post by TheLions on 2007-12-12
try find t a crack:

[http://www.google.hr/search?hl=hr&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=iM4&q=game+copy&btnG=Tra%C5%BEi&meta=](http://www.google.hr/search?hl=hr&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=iM4&q=game+copy&btnG=Tra%C5%BEi&meta=)

---

