---
title: "Civilization 5"
date: 2013-04-16
forum: Wine
---

### Post by Hoso001 on 2013-04-16
Hi everybody!

I am having a single issue running civilization 5 in wine. The game plays for a few mins, and the sound just dies. No error, the game still runs just completly muted. I am running Civilization V off of steam. Everything else is working fine with it. Does anyone have a solution for this problem?

I am running ubuntu 12.10 amd64 with wine 1.41. It winecfg is set to windows xp 


Thanks

---

### Post by Hoso001 on 2013-04-16
I found a possible fix but i am getting errors. 

I created a short executable script thingy to use the fix. The WineHQ notes on the games says that this might will help.

The Script is:

```

padsp wine "C:\Program Files (x86)\Steam\SteamApps\common\Sid Meier's Civilization V\CivilizationV.exe"

```

When I execute this I get the following error message,

```


david@david-box:~/Desktop$ ./Civ\ V.command
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/pulseaudio/libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.


```

Any tips on how to get this error fixed? Perhaps if i get this error resolved I will get to enjoy the nice soundtrack on the game :)


Thanks,

Hoso001

---

