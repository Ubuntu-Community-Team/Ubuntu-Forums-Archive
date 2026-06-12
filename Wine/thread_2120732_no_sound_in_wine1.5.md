---
title: "no sound in wine1.5"
date: 2013-02-27
forum: Wine
---

### Post by ss2pheonix on 2013-02-27
I have recently installed wine1.5 and was working on getting starcraft II working in it, I was able to get it installed and the game runs great but no sound. I get to looking into a fix and it seems that my version of wine has no audio drivers installed (picture of wine audio tab is attached), can anyone offer me somewhere to go from here? Sound is working perfectly everywhere in my system other than wine.
I am running linux mint 14 cinnamon x64
I have already posted this on the mint forums but these are more active so i decided to post it here too.
I have also looked through the stickies on this page but none of them seem to help.
[Here]("http://forums.linuxmint.com/viewtopic.php?f=47&t=126935&p=692593#p692593") is the original post on the mint forums where you can find the attached picture.

---

### Post by ss2pheonix on 2013-02-27
OK I solved it myself, it took a complete removal of wine1.5 and a fresh install which I used```
sudo apt-get install wine1.5-amd64
``` and all of the sound issues disappeared. I think I may have installed the 32bit version through the software manager on accident.

---

