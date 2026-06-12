---
title: "TES construction set (morrowind) problem"
date: 2008-08-13
forum: Wine
---

### Post by Champy on 2008-08-13
i just installed morrowind, and it runs very well. im pleased.
then i tryed using the constructon set, andi made a map where the ground texture was peter molyneux's face and tryed to save it to data files.

but when i try to save my work into data files, the program just closes. its quite annoying. any suggestions would be great.

-i am a champ

---

### Post by lycan91 on 2008-09-30
Yeah, i am having the same problem, everytime i trie to saves it crashes, and have to force quit or it shuts down. Any help would be great.

---

### Post by gruffy-06 on 2008-11-22
Just tried the Construction Set now, but no success. Tried with the stock version of Wine from the Ubuntu repos and the latest from a 3rd party repo, but CS still crashes whenever I try to save a plugin. It might be worth waiting a while until a fix comes up, as I'm clueless to what could be causing this.

EDIT: I've now acquired output from the console, included in the attached text file.

---

### Post by Sarrel on 2009-02-05
I've got the same problem. I thought it might just be my computers same overheating problem, because it has that problem with morrowind, but it doesn't actually shut down my computer, the cs makes this really weird high-pitched noise, then just closes while I'm working, or if I try to save. I enjoyed modding when this computer still ran xp, and I'd rather not have to reinstall it just for this one program. Any suggestions on how to fix it would be appreciated.

---

### Post by patros on 2009-07-24
To save your mods you need to enable the "autosave" feature (under File->Preferences). This bypasses where the crash is caused and will save your mod as "AutoSave.bak", simply rename to something like "Foo.esp" and you will be able to select it as a data file with the Morrowind Launcher.

---

### Post by paultag on 2010-02-01
Aye, I can confirm this works.

There are a lot of bugs, beware! There are tons of hidden failure points, something as small as clicking a menu item can fault the wine runtime.

I don't suggest hacking this around too much, it's very very buggy

---

