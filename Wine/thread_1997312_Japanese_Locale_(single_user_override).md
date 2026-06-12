---
title: "Japanese Locale (single user override)"
date: 2012-06-03
forum: Wine
---

### Post by Mackus on 2012-06-03
I want to add japanese locale to use with wine[FONT=monospace].
[/FONT]From what I found I have to do, normally I would type in in terminal:
*sudo gedit /var/lib/locales/supported.d/ja*
and write following lines to the file:
[I]ja_JP.UTF-8 UTF-8
ja_JP.EUC-JP EUC-JP[/I]
then I would type in terminal:
*sudo dpkg-reconfigure locales *
then run game with:
*LANG=ja_JP.UTF-8 wine d:\\directory\\game.exe* (how would I use it for other wineprefix?)
but I have no root access to do it, it says:
*mackus is not in the sudoers file.  This incident will be reported*
Is there way to override global locales for one user only?

---

### Post by Perfect Storm on 2012-06-05
Moved to wine section.

---

### Post by ntzrmtthihu777 on 2012-11-14
Also interested in running wine in Japanese. The version I have (1.4.1) is compatible with UTAU, but I must install it under a Japanese locale first, before I can install the English GUI patch.

[Edit]
I managed to do what I needed by running
```
LANG=ja_JP.utf8 wine utau0277inst.exe
```
maybe this will do the trick for you.

---

