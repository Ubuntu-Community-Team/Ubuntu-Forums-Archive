---
title: "Uninstalling Call of Duty 4"
date: 2008-02-25
forum: Wine
---

### Post by SoberWarlock on 2008-02-25
I'm currently trying to uninstall Call of Duty 4 under wine, but it does not seem to respond. How do I uninstall Call of Duty 4 using the Terminal?  :confused:

***Here is my Call of Duty 4 Dir Path****

```
/home/(user)/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare
```

---

### Post by SoberWarlock on 2008-02-28
So where should I be looking at to eliminate every single Call of Duty 4 files so I can re-install the game and start all over.....?

---

### Post by ahaslam on 2008-02-28
Are you trying to uninstall via a menu entry? They often don't work, the official procedure is to issue:
```
uninstaller
```
& select your application.

As far as CoD4 is concerned, it doesn't mess with the reg too much & only installs to its own dir. If the above doesn't work & you're reinstalling anyway, the following will do:
```
rm -r ~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare
```
;)

---

