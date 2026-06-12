---
title: "How to force unlisted WINE versions?"
date: 2007-11-01
forum: Wine
---

### Post by JusticeZero on 2007-11-01
I use WINE to play Dark Age of Camelot.
In 0.9.47, it has an issue with an invisible cursor. I updated to 0.9.48 in hopes this would help.

DAoC _DOES NOT RUN_ in 0.9.48. Specifically, the updater doesn't update, just sits as 'Checking for updates...' forever. It also did not run in 0.9.46 in conjunction with Ubuntu 7.10. When I went to try to force going back to the version that worked, it was not one of the options - only 0.9.46 and 0.9.48 are listed.

Any suggestions?

---

### Post by Colro on 2007-11-01
Uninstall your current version:

```
sudo apt-get remove wine
```

then install one that might work:
[0.9.47](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.47~winehq0~ubuntu~7.04-1_i386.deb)
[0.9.45](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb)
[0.9.44](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.44~winehq0~ubuntu~7.04-1_i386.deb)
[0.9.43](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.43~winehq0~ubuntu~7.04-1_i386.deb)

...I give up. You can find more listed [here](http://wine.budgetdedicated.com/archive/index.html). The ones listed under Feisty work just fine with Gutsy.

---

