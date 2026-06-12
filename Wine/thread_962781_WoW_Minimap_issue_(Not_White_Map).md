---
title: "WoW Minimap issue (Not White Map)"
date: 2008-10-29
forum: Wine
---

### Post by rpeals1 on 2008-10-29
Hey all i'm having some issues using WoW with Wine on ubuntu hardy heron. I've done research and all the information i'm finding has to do with minimaps going white when entering cities. i'm having a somewhat similar issue. whenever i go inside a city/cave/instance my mini map cuts to a 1/4 piece of the map and moves down and to the right. nothing that ruins the game i just get tired of being lost in instances from no mini map. 

I'm on an acer aspire ast180. Nvidia chipset. Nvidia Geforce 6100 Nforce 405. if you need to know anything else about my system just let me know i'm not exactly sure what's needed. 

Heres a screenshot of the issue. minimap works perfectly fine outdoors. Any help is greatly appreciated.

---

### Post by lH)4~mK0e on 2008-10-31
I had this problem when I didn't have the game running in opengl mode.

Run **gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf** and add this to the file at the bottom.

```

SET gxApi "opengl"

```

Hope this helps.

---

### Post by Laibcoms on 2008-10-31
> **miwarlock002 said:**
> I had this problem when I didn't have the game running in opengl mode.

Run **gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf** and add this to the file at the bottom.

```

SET gxApi "opengl"

```Hope this helps.


Or it could be lag between you and the server (and the client seems to be getting a lot of packet loss these days even under XP).

---

### Post by rpeals1 on 2008-10-31
That did it. thanks for the help.

---

