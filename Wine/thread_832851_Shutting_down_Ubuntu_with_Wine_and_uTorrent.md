---
title: "Shutting down Ubuntu with Wine and uTorrent"
date: 2008-06-18
forum: Wine
---

### Post by thing2b on 2008-06-18
Does anyone one know how I can get the "Shutdown when downloads complete" function working on uTorrent. It seems to shutdown uTorrent but I also would like it to shutdown Ubuntu?

Thanks for any help.

---

### Post by conscious on 2008-06-18
What about the simplest script?
```
#!/bin/bash
wine /your/path/to/utorrent.exe
shutdown -h now
```
This will shut down the system as soon as wine exits. Don't forget to make the script executable. The problem is that shutdown requires root privileges to work, but you may use [this workaround]("http://ubuntuforums.org/showthread.php?t=79508").

---

