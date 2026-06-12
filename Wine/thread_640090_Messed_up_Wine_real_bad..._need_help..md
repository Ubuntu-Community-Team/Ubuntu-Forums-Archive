---
title: "Messed up Wine real bad... need help."
date: 2007-12-13
forum: Wine
---

### Post by mbiebel872 on 2007-12-13
Ok, so at first I downloaded wine so I could get a nintendo 64 emulator running, in this case Project64. At first it was working fine. I was adding additional plug-ins to the emulator, and the emulator started freezing up trying to load the games. Then wine wouldn't run the emulator at all. So I decided to try to uninstall and re-install wine. That didn't work. Too make a long story short, I wound up deleting the windows folder, the program files folder, as well as the Wine menu in my applications menu. I figured if I did that, that it would re-install Wine and everything that came with it. It didn't.

So now, what I believe needs to be done is that I need to trick my Ubuntu system into thinking that Wine never existed in the first place, so that when I add/remove the wine package, it completely re-installs wine. 

Any suggestions/recommendations/instructions.... I'm all ears.

Thanks.

---

### Post by mbiebel872 on 2007-12-13
Well I managed to fix the whole /.wine/ directory... but I still have the problem with it no longer being in my applications menu. I suppose I could figure it out eventually, but if anyone has any advice let me know.

Thanks.

---

### Post by bastiegast on 2007-12-14
To fix wine you will never need to reinstall it. You will only have to remove your .wine directory. That will reset everything. If you want your menu items back, uninstall wine, then reinstall i guess.

---

### Post by cogadh on 2007-12-14
Do the uninstall with the "purge" option, then re-install and it should bring everything back:
```
sudo apt-get remove --purge wine
```
In the future, if you screw up Wine, you've only actually screwed up your fake Windows directory, Wine itself is untouched. Just do what bastiegast said and delete the .wine directory from your home folder, then run winecfg to create a new one.

---

