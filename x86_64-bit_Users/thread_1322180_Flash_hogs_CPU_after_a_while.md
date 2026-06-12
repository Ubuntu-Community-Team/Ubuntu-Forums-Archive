---
title: "Flash hogs CPU after a while?"
date: 2009-11-10
forum: x86 64-bit Users
---

### Post by space-litter on 2009-11-10
Hello, I have looked in other threads but the issues seem to be Flash not working. In my instance, it seems to be working fine.

However, as time goes on (multiple videos, or one long video, or lots of Flash usage in general) my CPU usage keeps going up and up until the entire system is bogged down. Only by restarting Firefox can I stop this, and even then as soon as I try to open another Flash app it goes right back to 100%. After restarting Ubuntu altogether it is back to normal.

The really strange thing is, I was having this problem when I was using 32-bit as well, although that was with Jaunty. I had hoped going to 64-bit with Karmic would help, but it's the same problem.

Any ideas?

---

### Post by bford16 on 2009-11-10
Try checking for multiple 'npviewer.bin' processes.```
ps aux | grep npviewer.bin
```  You can kill all Flash processes with ```
sudo killall npviewer.bin
``` (Requires you to enter your password for authentication.

---

### Post by space-litter on 2009-11-10
Thanks, that will be useful until there is a more permanent fix for this issue. Has no one else experienced this?

I read back when I was researching fixes for Jaunty that it was a kernel issue with the Intel integrated video card and that the new kernel shipped with Karmic would have a fix for it. Either that was not in fact my problem, or they were wrong about the new kernel.

---

### Post by markbuntu on 2009-11-11
It is most likely a memory leak, buggy flash. Clear your cache and restart firefox often.

---

