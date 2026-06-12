---
title: "DVDs Lag"
date: 2006-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by clumsychild on 2006-06-29
At the moment I just installed Dapper Drake, now I'm not new to Linux and have been using it for sometime and I don't have a slow system. I'll display the specs after this, but I'm having my dvds lag very badly to the point of where they aren't watchable. I was just wondering if anyone else was having this happen or if it has to do with something specific. Anything at all would be useful. I was using fedora core 5 before this and even though it was more difficult to get setup I did not have the amount of lag I have in Ubuntu.

AMD Athlon 64 2800+
1 gig of ram
ATI Radeon 9800 Pro 128MB
250 GB HDD

Now that more then tops the requirements, so I'm not sure what the problem is. I had this problem with the previous version of ubuntu as well. Normally Windows is slower then Linux, but at the moment x64 version of Windows is completely beating out Ubuntu, for load times, speeds etc.

---

### Post by scxtt on 2006-06-29
what do you get for "hdparm /dev/<cdrom device>"?

---

### Post by falcon15500 on 2006-06-29
I just saw a similar thread.  In that thread the OP noticed that his DVD drive was spinning down after a few minutes of play.  This caused the movie to lag as it had to spin back up to read the next part of the disc.  I suggested he try to use hdparm to change the spindown time.  ```
hdparm /dev/hdX -S 120
``` would change the spindown time to 10 minutes.

falc

---

