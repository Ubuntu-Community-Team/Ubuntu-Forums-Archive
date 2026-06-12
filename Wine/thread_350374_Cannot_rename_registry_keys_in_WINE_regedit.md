---
title: "Cannot rename registry keys in WINE regedit"
date: 2007-01-31
forum: Wine
---

### Post by cowuhsocky on 2007-01-31
Hello, I am new to the Ubuntu community so I will try to explain everything with as much detail as possible. After completing the setup of my last Ubuntu Edgy install, I set out to install games, the first chosen being World of Warcraft and Counter-Strike Source. After full installation of WoW the Wine AppDB website requires that you must disable extensions in regedit by adding a new key and string value. ([http://appdb.winehq.org/appview.php?iVersionId=5606)](http://appdb.winehq.org/appview.php?iVersionId=5606)). The very first time I accessed this manager I was able to complete the task and rename "New Key #1" to opengl as informed, but for every attempt after this, and even after a complete hard drive wipe and reinstall of Ubuntu Edgy, I still cannot rename the registry keys to add the required extensions to my WINE regedit. Any help will be happily welcomed, as I am getting quite frustrated with this predicament. 
Thank You,
    ~Cowuhsocky

---

### Post by cdevilrun on 2007-01-31
Sorry to get you excited with a reply to your post.
Just wanted to say that the same exact thing is happening to me and I feel your pain. I recently updated wine and I think this is a symptom of that upgrade. I'll head over to their bug forums and post our problem.

edit: The wine crew is on it. [http://bugs.winehq.org/show_bug.cgi?id=7280](http://bugs.winehq.org/show_bug.cgi?id=7280)

---

### Post by hikaricore on 2007-01-31
This may not help, but if you have upgraded wine or have issues with your wine directories, run:

```
wineprefixcreate
```

From a terminal.  This _shouldn't_ affect any of your settings it will just clean up a few things to make sure everything is setup as it should be.

---

### Post by cowuhsocky on 2007-01-31
Well thanks a lot cdevil, but does this mean that we will simply have to wait until the next version of WINE? Or is it something odd with our coding...because it seems as though not very many people are having this problem.

---

### Post by cdevilrun on 2007-01-31
No no, read the responses. If you expand the field horizontinally until the scroll bar disappears you can rename the key. I just did it. Good luck.

---

### Post by cowuhsocky on 2007-02-01
Excellent! That fix works perfectly. Thank you very much to both of you. Hopefully this will lead to fixes for everyone else having this problem.
Cheers,
Cow

---

### Post by Sammi on 2007-02-01
I also had this problem. Only I kept on tinkering with regedit, trying to edit other keys, then suddenly it worked after a few minutes. I must have expanded the hierarchical field without noticing :D

Seems like a very small and precise bug. There shouldn't be much code in Wine that can be suspected to be the culprid of this bug.

---

### Post by malleus74 on 2008-10-24
This problem is still not resolved

---

