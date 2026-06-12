---
title: "Skyrim~ do or do not,there is no try"
date: 2012-05-11
forum: Wine
---

### Post by ZaMonk on 2012-05-11
Hey,

So i just instaled Skyrim via wine, and its lagging very bad,like 6 mine to start new game bad.it ran perfectly on win.any suggestion on fixing or should i just dual system it?

my speks
Intel E570 3.00Ghz
2gb Ram
ati radeon 2600 HD



PS:freshly migrated

---

### Post by Enigmapond on 2012-05-11
Yea I tried as well with no love. Probably one of the only reasons I keep Windows around. Morrowind I got to work but not this...yet.

---

### Post by ZaMonk on 2012-05-11
> **Enigmapond said:**
> Yea I tried as well with no love. Probably one of the only reasons I keep Winblow$ around. Morrowind I got to work but not this...yet.


thx mate (mmmm, morrowind)

---

### Post by Enigmapond on 2012-05-11
Morrowind is easy now. As long as you have it installed...anywhere you can play it very well on ubuntu with openmw...

[http://openmw.org/en/](http://openmw.org/en/)

---

### Post by Oscailt on 2012-05-11
Skyrim is very new so I would never have expected it to work under Wine. Hopefully when Ubuntu becomes more main stream it will see an increase into support for linux gamming.

---

### Post by rai4shu2 on 2012-05-13
With a card that old, you'll need to disable a lot of the features like shadows and such. If you can find Skyrim.ini, try adding some of this:

> [LightingShader]
fDecalLODFadeEnd=0.0
fDecalLODFadeStart=0.0
fEnvmapLODFadeEnd=0.0
fEnvmapLODFadeStart=0.0
fEyeEnvmapLODEnd=0.0
fRefractionLODFadeEnd=0.0
fRefractionLODFadeStart=0.0
fSpecularLODFadeEnd=0.0
fSpecularLODFadeStart=0.0

Look for that shadow disable mod on the Nexus, as well.

---

