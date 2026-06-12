---
title: "World of Warcraft Not remembering me"
date: 2008-04-13
forum: Wine
---

### Post by eccheng on 2008-04-13
Hi!  I am a happy wow gamer that has one small annoying problem after the installation.  Everything works fine.  Music, graphics gameplay work flawlessly.   The only problem i seem to have is that whenever i log into the wow game, it forgets me.  All of the sound/interface options, quest texts and settings that I personally wanted would all reset to default everytime I log on.  Even my screen name.  I've tried clicking Remember my name on the lower left hand corner, but it doesn't work.  I can't figure out how to get the game to memorize my perferences.  
I've run prior installations of wow on ubuntu and this is the first time it's happened to me.  Any ideas?

---

### Post by eccheng on 2008-04-15
Bump.


Maybe I should just reinstall?  Any help would be appreciated.

---

### Post by Melhisedek on 2008-04-16
Do you have 2 instances of Config.wtf in your wow directory? One in main map and one in WTF folder if I remember correctly...

In any case I had the same problem and it was caused by following the wow guide that made me create a Config.wtf in main directory with those 3 lines in it. It seems it somehow deleted the original Config.wtf found in WTF folder everytime I started new game or at least game reset it.

In any case I just found the other Config file and put those 3 lines in the top of that file, and deleted the file in main directory. 

Since than everything has worked fine and dandy *knock on wood* ;)

---

### Post by jesusfreak107 on 2008-04-16
> **eccheng said:**
> Hi!  I am a happy wow gamer that has one small annoying problem after the installation.  Everything works fine.  Music, graphics gameplay work flawlessly.   The only problem i seem to have is that whenever i log into the wow game, it forgets me.  All of the sound/interface options, quest texts and settings that I personally wanted would all reset to default everytime I log on.  Even my screen name.  I've tried clicking Remember my name on the lower left hand corner, but it doesn't work.  I can't figure out how to get the game to memorize my perferences.  
I've run prior installations of wow on ubuntu and this is the first time it's happened to me.  Any ideas?
> I've run prior installations of wow on ubuntu and this is the first time it's happened to me. Any ideas?
Did you update Wine?  This may be the problem, every version of Wine runs different games differently.  If your version of wine works, it is not a good idea to update it.  If that was your problem, try reinstalling the versionof Wine that it worked on.

---

### Post by eccheng on 2008-04-19
> **Melhisedek said:**
> Do you have 2 instances of Config.wtf in your wow directory? One in main map and one in WTF folder if I remember correctly...

In any case I had the same problem and it was caused by following the wow guide that made me create a Config.wtf in main directory with those 3 lines in it. It seems it somehow deleted the original Config.wtf found in WTF folder everytime I started new game or at least game reset it.

In any case I just found the other Config file and put those 3 lines in the top of that file, and deleted the file in main directory. 

Since than everything has worked fine and dandy *knock on wood* ;)



It works now!!!  Awesome!!!  thank you very very much!!  you're the best!!  =)

---

