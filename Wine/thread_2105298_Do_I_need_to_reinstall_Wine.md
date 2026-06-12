---
title: "Do I need to reinstall Wine ?"
date: 2013-01-15
forum: Wine
---

### Post by grey1beard on 2013-01-15
I've been trying to install an old copy of Dragon Naturally speaking ver 5 on my ubuntu 12.04 lts via Wine 1.5.21 on a 64bit pc.

All was going swimmingly, until a 'register now' window popped up, and everything froze.
I used the Ctrl-PrtSc-Alt-reisub method to escape, then after rebooting tried again. Various attempts followed to try both uninstalling/repairing/modifying the installation, but at some stage(variable) the mouse freezes.

I've read various threads concerning the general approach to removing packages, but I would like to know if the simplest might be to remove Wine and reinstall it.
My reasoning is that one consistent pop up I get says

> C:/windows/ is either a root directory or is reserved for Windows use.
Please select a different directory to install Naturally Speaking

so I assumed that a deletion/reinstall might clear this, as I can't see how I can choose another directory ?

Please advise,
Regards
John

---

### Post by Lila7714 on 2013-01-18
I don't think you'll need to reinstall wine because all your locale files will remain.
If you wanna do-over the installation just delete ~/.wine or if you put somewhere else then there.

The error message you are receiving could possibly be because it won't allow you to install in that directory C/windows. Try program files or something.

---

### Post by grey1beard on 2013-01-19
Thanks Lila7714.
Yesterday I discovered 'Playonlinux', so I might try that as an alternative route to getting DNS on board.

Either way, persistence usually pays ;)
John

---

### Post by Mark Phelps on 2013-01-21
Sorry to tell you this, but the WineHQ site rates DNS v5 as Silver -- meaning, there are major features that do not work (otherwise, it would have been rated Gold or Platinum):

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077")

PlayOnLinux might help, but with this low a rating, it's not likely to make a difference.

---

### Post by grey1beard on 2013-01-21
Hi Mark.
Yes, I was aware of the 'Silver', but being an optomist I thought that as I had a copy of 5, I would give it a try.
The tests posted on that page are pretty ancient, so who knows what might have progressed since then ;).
Finding playonlinux, with its auto selection of an apropriate wine version, might also have a bearing on a better outcome.

Regards
John

---

