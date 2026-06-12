---
title: "Hung at splash screen"
date: 2006-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by PaulB007 on 2006-05-04
Im running a 500 MHZ Imac with 128 MB ram. I am installing Ubuntu on this machine. I ran it on another one 350 MHZ with 64 ram and it ran. Now when I login it hangs and hangs and doesnt boot, it loads so slow, it takes about 15 minutes to even have the stuff start loading. I've reinstalled 5 times, I dont understand the problem. I have even gone into console mode and upgraded to Kubuntu but it did the same thing. Also, if I wait long enough I see a small black area with white text that says "Update Notifier" and it has three icons off to the side. A bar with a black foot on it, an icon with a peice of paper and a pencil off to the right, and then one with a floppy and CD in it. Any ideas on how to get it working right?

---

### Post by 3rdalbum on 2006-05-04
It may be a problem with DRI. Go into the console and type:
```

sudo nano /etc/X11/xorg.conf

```

And put a hash (#) before the line that says "Load dri". Save your changes, restart Ubuntu, and see if that works.

Just to clarify: Are you having these problems on the 64 meg iMac, or the 128 meg one?

---

### Post by PaulB007 on 2006-05-04
Problem solved, thanks.

---

