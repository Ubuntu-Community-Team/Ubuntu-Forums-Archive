---
title: "wine: age of mythology issues?"
date: 2008-10-23
forum: Wine
---

### Post by hallowname on 2008-10-23
Hello, I've been through yokozar's checklist, appdb, fedora forums, linuxquestions, and wine's bugzilla... If anyone at all has seen this message: 

"Cannot create log file, please make sure that you have full rights on the directory that you installed Age of Mythology into, and that you have available disk space. Error access denied."

from Age of Mythology and fixed it, please let me know... I've seen numerous screenshots of this app working perfectly (platinum rated twice), yet no wine version, winetricks hacks, cedega, crossover, nothin... they all show this error... not only that, but how did this game get a platinum rating twice... i've tried wine development, wine stable (1.0&1.0.1), and both wine versions that recieved platinum rating. A bug has been sitting on the wine-bugzilla since march of the same issue, yet people have (recently) installed and played this game fine... there was a unsolved thread on this topic that the ubuntuforum moderators felt was necessary to mark read-only before the issue was resolved...

any help at all would be greatly appreciated...

note: this is for the common good, i don't play closed source games...

---

### Post by rocky5051 on 2008-10-23
Where do you encounter this error? That sounds like something that would happen after an error. I know the game crashes when you finish playing it with an error message but I've never ran into that before.

Try installing Wine 1.1.6 (again if you aren't using that version currently), make sure you are using a fixed, No-CD exe for the game for the game (since the game will not detect the CD when starting up), and if those steps fail run this command.

```
wineboot -esr
```

Also, if you are trying to run wine as root that may result in that error.

---

