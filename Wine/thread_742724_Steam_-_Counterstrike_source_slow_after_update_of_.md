---
title: "Steam - Counterstrike source slow after update of wine compiled"
date: 2008-04-02
forum: Wine
---

### Post by arrakis31 on 2008-04-02
Hi,

I am running counter strike on my xps 1330 with the 8400 GS and 4 g of ram.
I have run css with no problem under the default wine version for ubuntu 7.10 x64 after installing with sudo apt-get install wine ....

I wanted to try Call of Duty 4 (demo) so I have compil the last wine GIT following the different howTO ... no probl CoD4 works like a charge.

However after starting Steam in the new wine, the game is slow like hell
I have no idea why ???

{updated}
I think it might be a directx problem. Call of Duty 4 required the installation of directx, which I have done.
But I think it kill the setup of counter strike ?????

---

### Post by arrakis31 on 2008-04-02
Bump

---

### Post by aoanla on 2008-04-02
A note: In general, it is a Bad Idea to install copies of DirectX in Wine - Wine has its own versions of these libraries which should not be overwritten (except in very particular cases).

As far as I can tell from the AppDB entry for CoD4, while you may need to patch Wine (which I assume is why you were building it from source), you don't need to install DirectX.

Therefore, I suggest that you attempt to remove the DirectX libraries you installed (obviously, the quick way would be to delete and recreate your .wine folder, but there's almost certainly a better way...)

---

### Post by arrakis31 on 2008-04-04
Could it be cause by the 3Dmark patch applied to get call of duty running ????

---

