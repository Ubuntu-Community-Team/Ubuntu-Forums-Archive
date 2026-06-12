---
title: "A quick performance-improving note"
date: 2008-03-29
forum: Wine
---

### Post by jjk7288 on 2008-03-29
I recently posted a thread on how my 8800GTX gets beat pretty hard by World of Warcraft in WINE, but I've noticed that updating drivers (via Envy) instead of using the one's provided by Ubuntu's Restricted Driver Manager seems to improve performance quite a bit, as well as fixing various graphical glitches.

Anyone who has not done so, I'd strongly recommend [downloading Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to update your drivers. It worked well for me.

---

### Post by el_ricardo on 2008-03-29
yeah, envy's a nice little program, get's the very latest proprietary drivers from the nvidia website, automates the .run file complete with dependencies, much better than what's available via apt-get. There are only 2 problems with it, one being that you have to make sure you uninstall the drivers via envy before you do a kernel upgrade (I've forgotten to do this several times now). The other being that it's terrible at sorting out ATI drivers, which was annoying to find out when I just got a new gfx card (ATI).

---

### Post by Melhisedek on 2008-03-31
What are the latest Nvidia drivers supported by Envy?

---

### Post by jjk7288 on 2008-03-31
It downloads the latest ones from nvidia during install.

---

### Post by Sockerdrickan on 2008-04-01
I always install them manually, I hate dependencies.

---

### Post by jjk7288 on 2008-04-01
> **Tux0r said:**
> I always install them manually, I hate dependencies.

The Nvidia installer seems straightforward enough, but I've always borked my X Windows when using it.

---

