---
title: "emac g5 1gz"
date: 2006-04-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by dq101 on 2006-04-11
will it work for that computer i tryed once and affter a few minutes useing live edition it went blank screen on me?

---

### Post by mscman on 2006-04-11
I've never tried running Ubuntu on a Mac, but it seems the computer should meet the requirements for the PPC version of Ubuntu.  Perhaps the live CD was faulty...:-k

---

### Post by 3rdalbum on 2006-04-11
It's not faulty, you just need to run the Expert mode. Press Tab at the yaboot prompt, and you'll see options like "expert-powerpc-64". Type in whatever that one is, and press Return.

When asked if it should do monitor autodetection, say NO. Choose the "Advanced" method of setting the monitor settings. When it asks you for the HorizSync, type in 60-60. When it asks for the VertRefresh, type in 75-117. When it asks if you want to use DRI, choose NO.

If it still doesn't work, you may need to specify your video card manually as well rather than do autodetection. In this case, you would need to choose "ATI" from the menu.

---

### Post by dq101 on 2006-04-12
I did what you told me to do but when it got to the loading screen it stoped loading, ejected disk and restarted my emac?

---

