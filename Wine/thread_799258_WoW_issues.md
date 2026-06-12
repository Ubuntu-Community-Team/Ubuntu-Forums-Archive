---
title: "WoW issues"
date: 2008-05-18
forum: Wine
---

### Post by malfist on 2008-05-18
Since I updated yesterday (including a kernel update I believe), it is near impossible to play WoW.

The screen gets a lot of lines that are blurs all over it and then everything freezes, no exit, no control. WoW music still plays but that's it. I can use the "Magic Keys" to reboot but I can't switch TTY or restart X.

Any suggestions? I've already reset settings in the Config.wtf

---

### Post by igster on 2008-05-19
If you did a kernel update and are using a binary driver with kernel module(s) like nvidia you may have to [rebuild the kernel module(s)]("https://help.ubuntu.com/community/NvidiaManual").  Are you experiencing any other problems with video?  Do you have any other 3D apps, like another game perhaps, that you can test?

---

### Post by malfist on 2008-05-19
I'm using nvidia-glx-new or whatever that package is. I didn't use nvidia's installer. I have a few other 3D apps, but none of them run under wine. I'll do some testing.

My video card is GeForce 6800.

---

### Post by malfist on 2008-05-19
Yes, it is not isolated to WoW, tremulous crashed in exactly the same way. I'll repost this with a more specific title in a more proper area (I.E. Graphics/Multimedia forum)

---

