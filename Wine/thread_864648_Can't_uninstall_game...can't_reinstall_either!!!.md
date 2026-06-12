---
title: "Can't uninstall game...can't reinstall either!!!"
date: 2008-07-19
forum: Wine
---

### Post by penncon on 2008-07-19
Okay, I'm trying to install Command & Conquer 3 and was having problems.  I found some ideas, but wanted to start from a clean install of the game, so I uninstalled and was planning on reinstalling after patching wine.  It wouldn't uninstall, but now every time I try to reinstall the game it detects the old installation and my only options are to Modify my install (which won't work) or to Remove (which doesn't actually remove).  Is there somewhere in the registry or something where I can tell it that the game isn't installed so that I can reinstall?  I know have a game that won't uninstall and doesn't work, either.

Thanks in advance.

---

### Post by LinuxRocks713 on 2008-08-03
> **penncon said:**
> Okay, I'm trying to install Command & Conquer 3 and was having problems.  I found some ideas, but wanted to start from a clean install of the game, so I uninstalled and was planning on reinstalling after patching wine.  It wouldn't uninstall, but now every time I try to reinstall the game it detects the old installation and my only options are to Modify my install (which won't work) or to Remove (which doesn't actually remove).  Is there somewhere in the registry or something where I can tell it that the game isn't installed so that I can reinstall?  I know have a game that won't uninstall and doesn't work, either.

Thanks in advance.

Delete and move your wine prefix. It will create a new/fresh one for you:

```

mv ~/.wine ~/oldwineprefix

```

Then run your game again.

---

### Post by Mecanicu on 2010-03-24
I have the same problem, the code does not help.

---

### Post by donkyhotay on 2010-03-24
Deleting your .wine directory removes all windows programs installed with wine. If you're not able to re-install it I don't know why but on the other side there is nothing to uninstall anymore.

---

