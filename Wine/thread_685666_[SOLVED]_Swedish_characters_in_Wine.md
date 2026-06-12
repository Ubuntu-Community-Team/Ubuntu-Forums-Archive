---
title: "[SOLVED] Swedish characters in Wine"
date: 2008-02-02
forum: Wine
---

### Post by keelon on 2008-02-02
Hello, 

Having trouble with Swedish characters in Wine. I can see them, but I can't type them. Hiting the Å Ä Ö keys gives me nothing at all.

I can't find any info about Wine and changing locale or language anywhere.

I've tried it in Wine's Notepad just to be sure, but nothing.

I've even tried Crossover, but the program I need dosen't work in Crossover. It works nicely in Wine, it's just that I can't type the Swedish characters

Solutions anyone?

---

### Post by Sockerdrickan on 2008-02-02
That was a very weird bug, it works for me.
File a bug to the wine developers and they'll fix it!

---

### Post by keelon on 2008-02-02
I've solved it!

I suspected that it had something to do with locale. I checked my settings, and it appered to be correct. But when I typed in this command

echo $LANG

I got an strange output 

sv_FI.UTF-8@euro (should have been sv_SE.UTF-8)

I later found the faulty setting. In $HOME/.dmrc

---

