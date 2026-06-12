---
title: "need help with my game please...."
date: 2008-04-26
forum: Wine
---

### Post by amyfan on 2008-04-26
here is what i get after removing wine and reinstalling it [http://paste.ubuntu-nl.org/64600/](http://paste.ubuntu-nl.org/64600/)   then i did dmesg in the term after the errors and this is what i get [http://paste.ubuntu-nl.org/64601/](http://paste.ubuntu-nl.org/64601/)


i removed wine because i only thought i would use it for wmp for xp but i found a better app then i removed it via sudo apt-get --purge remove wine 
then i used the synaptic to reinstall it got that error, then i done alt f2 typed nautilus and hit cntrl+h and deleted the .wine folder thinking it would rewrite the whole ordeal but same error.

---

### Post by FrozenFox on 2008-04-26
Are you trying to run a game in DOS? If so, I'd suggest you use DOSBOX instead of Wine. I recall seeing an error similar to this a few days ago in another message regarding the dos deal.

If that's not the case, try finding the files mss32.dll and binkw32.dll on the net (or from your copy of windows if they are win files) and put them in the appropriate folder (copy them to both your game directory and /home/YOURNAME/.wine/drive_c/windows/system32 perhaps?).

If this is the game youre trying to play, maybe this link might help..
[http://playubuntu.com/linux-games-/202.html](http://playubuntu.com/linux-games-/202.html)
Note you can install older versions of wine via the program PlayOnLinux, while keeping your current system wine unaffected. However, I suspect you will still need those 2 dll's (possibly others too) either way, as your first error log says; it can't find them.

---

### Post by amyfan on 2008-04-27
Frozenfox thank you for your help but none of that worked what did work was updating it to .60 from .59 now that did fix the problem [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) is the site i used to upgrade it...

---

