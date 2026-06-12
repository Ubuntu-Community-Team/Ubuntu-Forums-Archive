---
title: "Doom (2016) will not start on wine"
date: 2017-10-27
forum: Wine
---

### Post by thebestname21422 on 2017-10-27
Hello, I am new to this forum, I have been trying to figure out an answer to my question for a while now, I can't figure it out. The issue I am having is with the steam game Doom (2016)

So I have a Steam 64 Bit installation on PlayOnLinux Doom used to just launch just fine in it on OpenGL (Vulkan was slow for me) Now when I try to run Doom it says running for about half a second, then it says Syncing then it stops, the last thing I remember doing is upgrading from 17.04 to 17.10 This is the only game I am having a issue with. There is also nothing in the PlayOnLinux Debugger. I can not figure this out for the life of me, Help would be greatly appreciated ;) This is aggravating me so much because I was just at the end of the game too :KS

---

### Post by fredwntr1 on 2017-10-29
Did you mess around with winetricks previously and also did you verify the game files in steam?

---

### Post by fredwntr1 on 2017-10-29
on the game under steam right click and select launch options and add +r_renderAPI 0 that will revert back to openGL

---

