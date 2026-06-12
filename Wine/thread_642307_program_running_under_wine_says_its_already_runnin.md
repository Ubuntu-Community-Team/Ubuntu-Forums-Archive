---
title: "program running under wine says its already running, but I dont see it."
date: 2007-12-16
forum: Wine
---

### Post by lordvolo on 2007-12-16
program running under wine says its already running, but I dont see it. and the wine task manager does show it.

---

### Post by cogadh on 2007-12-16
Wow, that's interesting. :-k

Was there a question to be asked here? :?:

If you want to know how to fix it, we will likely need a lot more information, like what is the name of the program you are trying to run, what Wine version are you using, what errors have been produced by Wine in the terminal, etc.

---

### Post by lordvolo on 2007-12-16
Its the Steam client for windows. I'm using the latest version of wine, I think.

---

### Post by cogadh on 2007-12-16
You probably minimized the client window. Don't ever do that, you can't maximize it again because it is supposed to minimize to the tray icon, rather than the "task bar" (Wine doesn't seem to handle that correctly). Just open a terminal and type "wineserver -k" to kill all open Wine sessions, then re-launch the Steam client.

---

### Post by lordvolo on 2007-12-16
I killed the wineserver, and started the steam client again and the same thing happened.

---

### Post by cogadh on 2007-12-16
If it is giving you an error message that Steam is already running, then there are two things that you can do to fix it. First, update to the latest Wine (that error doesn't generally happen in the current Wine). Follow the instructions here to update to the current version:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

If that still doesn't fix the problem, then run Steam from the terminal like this:
```
nice -n 19 wine Steam.exe
```

---

