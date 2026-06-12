---
title: "[SOLVED] Wine changes my screen's resolution after I exit Warcraft 3"
date: 2007-12-02
forum: Wine
---

### Post by hotweiss on 2007-12-02
Wine changes my screen's resolution after I exit Warcraft 3. My screen resolution is 1400x1050 but I like to have it at 1024x768. When I exit Warcraft 3 my screen resolution automatically changes to 1400x1050. Any ideas?

---

### Post by cogadh on 2007-12-02
Edit your xorg.conf and remove the resolutions you don't want. I only keep 1024X768, 800X600 and 640X480 in mine (with multiple refresh rate entries for each). That way I have all the major resolutions needed by most games and the desktop is never set higher than the max that I prefer, 1024X768.

---

### Post by hotweiss on 2007-12-02
Thanks, that worked. I just changed my screens resolution to 1024x768.

---

