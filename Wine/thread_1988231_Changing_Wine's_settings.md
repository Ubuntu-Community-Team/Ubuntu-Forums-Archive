---
title: "Changing Wine's settings"
date: 2012-05-27
forum: Wine
---

### Post by Colo2 on 2012-05-27
Hey all.

I downloaded wine 1.4, and along with it came the setting.. Wine configuration. I then downloaded playonlinux and it proceeded to download & install another version of wine. Now, it's using that version of wine whenever I launch a game from it. My question is, how do I modify THAT version of wine, as it doesn't seem to have a config with it.

Tom

---

### Post by Toz on 2012-05-27
It's a little hidden and as you've noticed, the wine version is specific to the game you've installed. In the main PlayOnLinux window, click on the game to select it, then click on the "Configure" button. Go to the "Wine" tab and click on "Configure Wine".

---

### Post by Colo2 on 2012-05-27
brilliant, thank you sir :)

---

### Post by oldos2er on 2012-05-27
Moved to Wine.

---

### Post by Dlambert on 2012-05-28
Please mark as solved. And for system WINE:

```
winecfg
``` from terminal

---

### Post by Toz on 2012-05-29
> **Dlambert said:**
> Please mark as solved. And for system WINE:

```
winecfg
``` from terminal

This won't work for PlayOnLinux (POL) as POL creates specific wine prefixes (~/.PlayOnLinux/wineprefix) for each game. If you run just "winecfg", you'll be running the wine configuration utility against the default prefix only (~/.wine).

---

### Post by Dlambert on 2012-05-30
> **Toz said:**
> This won't work for PlayOnLinux (POL) as POL creates specific wine prefixes (~/.PlayOnLinux/wineprefix) for each game. If you run just "winecfg", you'll be running the wine configuration utility against the default prefix only (~/.wine).

Yes, that's why i said System WINE. Non-POL

---

