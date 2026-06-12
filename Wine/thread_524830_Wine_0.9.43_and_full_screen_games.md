---
title: "Wine 0.9.43 and full screen games"
date: 2007-08-13
forum: Wine
---

### Post by Teefs on 2007-08-13
I have recently installed Wine 0.9.43 and I am having some trouble with full screen games not using the whole screen. Some of the games I am running only support 640X480 resolution. Since my desktop is 1280 X 800 the games appear in a small 640X480 rectangle in the top left-hand corner of the screen with the rest of the screen black. Is this normal? Can I fix this?

---

### Post by cogadh on 2007-08-13
Do you have "Emulate virtual desktop" enabled in winecfg? If so, disable it. Also, is 640X480 one of the resolutions listed in your xorg.conf?

---

### Post by Teefs on 2007-08-13
Well I fixed the problem... I am not sure what caused it though. I edited the xorg.conf and then restarted but grub broke for some reason. I thought it would just be easier to reinstall Ubuntu than try to fix it.

Well... at least it works now.

---

### Post by Sammi on 2007-08-14
That's called the "nuke" solution. It's terribly effective ;)

---

