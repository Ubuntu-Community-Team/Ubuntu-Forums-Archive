---
title: "The Orange Box in Kubuntu?"
date: 2008-01-25
forum: Wine
---

### Post by person_99 on 2008-01-25
I am planning to purchase The Orange Box (Half life 2 engine stuff tossed together: Half life 2, Half life 2 EP1, Half life 2 EP2, Portal, Team Fortress 2, $50...wow.)
I have a few questions about running it through Wine on Kubuntu.

I will have Kubuntu Feisty Fawn when and if I attempt to install this via wine. 
I have Windows 2000, but Windows is...Uhg...Windows. I hate Windows.

Should the games from The Orange Box run well through Wine?
Are there any known bugs/problems?
Do the games require steam?
If so, can steam be used well through wine?

---

### Post by KThrace on 2008-01-25
I haven't tried it, but I've heard the Orange Box games + Steam work very well in WINE. You still need to use Steam, but given it's the base for all these games it's well supported in WINE.

I recommend reading this first, it will tell you how to get Steam working:
[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

Once Steam is working properly, you can then turn your attention to the individual games in the orange box. Search them using the "Search" box in the link.

---

### Post by person_99 on 2008-01-25
Steam and Half Life 2 are gold.
I couldn't find Portal or Team Fortress 2 on there, but I assume that they should do fine considering they are all the HL2 engine.

I now need Windows for the following:...?

:guitar:ROCK ON LINUX:guitar:

I post my results when I get the game. If all is good, I will probably use the Windows cds for skeet shooting target practice.

---

### Post by KThrace on 2008-01-25
Well, here's the thing: Portal and TF2 use a version of the HL2 (Source) engine that's far more advanced than what HL2 originally started out with. They're far more demanding and use many more shaders and advanced effects than HL2 does, particularly in Episode 2. So just because they all use the Source engine, doesn't mean they use it equally, I think needs to be said.

Having said that, I did the search for you:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9432](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9432)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9207](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9207)

---

### Post by person_99 on 2008-01-25
I see now. Thanks for the help.
It seems that Wine 0.52 (My version) performs well on those (Except TF2, which only has up to 0.46, but still.). Even games rated silver I have played through wine before still have much better performance then playing them in Winshi--err Windows.
The only game I recall having worse performance then in Windows was Bioshock. In Windows it actually let me click "Next" before crashing. :mad:

---

### Post by eljoeb on 2008-01-25
> **person_99 said:**
> I see now. Thanks for the help.
It seems that Wine 0.52 (My version) performs well on those (Except TF2, which only has up to 0.46, but still.). Even games rated silver I have played through wine before still have much better performance then playing them in Winshi--err Windows.
The only game I recall having worse performance then in Windows was Bioshock. In Windows it actually let me click "Next" before crashing. :mad:

I wouldn't expect that.  The Source engine games (HL2, Portal, TF2) run substantially worse than in Windows.  If you have a beefy computer, this may not matter as much, but you will still need to dial down the dxlevel to get compatibility.  Performance in HL2 ep2 was so bad that I reinstalled windows just to play it.  .  Bottom line for me: it works, just not great.  Its kind of annoying dialing down the detail when you know your computer can handle max settings in Windows.

---

### Post by person_99 on 2008-01-25
I have had problems with WoW come to think of it, but I just had it run in OpenGL and it killed all my problems, including FPS. 
I do have a computer far over the recommended for those games, if I'm not lucky I may have to spend 3 seconds to make it run in OpenGL.

I did Oblivon through wine fairly recently:
In Windows, I got around 20-30FPS with some graphical issues on Low at 800 x 600 no AA.
In Kubuntu through Wine 0.9.52, I got a constant 40fps with no graphical issues on High at 1024 x 768 with 2x AA.

Most other games do the same for me.


Because I don't trust Wine to perform well (Even though my hopes are up), I won't be uninstalling Windows until after I test the Orange Box on both operating systems when I get it. If Linux performs too bad, I will have to keep Windows.
I will post my results.

---

