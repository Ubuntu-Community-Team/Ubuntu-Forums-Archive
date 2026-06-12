---
title: "DirectX issue ( really wierd)"
date: 2008-02-14
forum: Wine
---

### Post by LeXrius on 2008-02-14
ok so i download wine, installed steam flawlessly run my games perfectly but,

all my source games detect my card @ directx 8.1 or somthing, but yet my card supports directx 10 :confused: 

and yes, i do have the drivers installed.

any idea's?

---

### Post by derjames on 2008-02-14
DirectX 10?... I think it is not implemented yet... please see the following webpage from the WINE project

[http://www.winehq.org/site/status_directx](http://www.winehq.org/site/status_directx)

---

### Post by LeXrius on 2008-02-14
Thanks for the reply, But what i ment was my card is able to run DX10 but i am not able to set DX10 mode in any source powered game

and i just remembered, dont i need to extract dx9.dll somewhere?

---

### Post by RemmyLee on 2008-02-14
DirectX support isn't based on what your card is capable of, it's based on what has been implemented by the wine team. Some DX10 features are coming down the pipline already, but since most games that support DX10 have DX9 support as well, it'll probably be awhile before we see a large amount of it implemented.

---

### Post by LeXrius on 2008-02-14
thanks for the reply,

but what i mean is i relize dx9 is working in wine but it detects my card at DX8.1 

but i did put -dxlevel 90 in the set launch options and that worked, but it starts in fullscreen and when i change settings and restart the game it dosent save what i change it too

it is really wierd.

---

### Post by aoanla on 2008-02-15
It's not that weird - Wine doesn't support all of DX9 yet, although it supports almost all of DX8 (and certainly the bits of DX8 used by most software). Hence, some games will detect Wine as providing only DX8 support, which is much safer from a compatibility perspective.
If you force DX9, then it'll work, mostly, although depending on which features your software needs, you'll get various bugs (for example, Source engine games seem to have problems displaying HUD items using Wine's current DX9 implementation).
DX10... isn't supported at all by Wine at present (although, of course, it's on their list, presumably once they get DX9 in better shape...).

---

### Post by bastiegast on 2008-02-15
DirectX 9 in source games is reasonably well supported. Your card won't be detected as dx10 capable since wine doesn't support that yet. DX9 mode in the latest generation source games(HL2:EP2 Portal TF2) is still very laggy but does work. In the older source games DX9 works except maybe for HDR.

To make it work you need a new version of wine (using these instrudtions: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)) you don't need to change any default settings, did you change any registry keys concerning directx? If you don't know what I mean then don't bother, it shouldn't be needed. If necessary, run with -dxlevel 90.

---

