---
title: "Steam dies at 26%"
date: 2006-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Wafflesomd on 2006-08-21
Well, I got wine installed nice and easy thanks to, um, well, I cant recall his name off hand, but the link was in his sig!

Anyways, I dl'd steam, installed it, and then it went to update, but seems to just stop at 26%, and then close itself.

I've checked wine's website, and it seems to be  common issue, with no solution.

---

### Post by Brownedwg89 on 2006-08-21
heres a good howto
it also addresses the 26% issue
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games#crash26](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games#crash26)

---

### Post by Wafflesomd on 2006-08-21
Well, I installed the font.  And that seemed to make it work, then ubunut froze, and well, it doesnt work anymore.

---

### Post by Brownedwg89 on 2006-08-22
did you type
```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```

---

### Post by Wafflesomd on 2006-08-22
Yah, "Moduale not found"

Which I assume means I should edit the directory where my steam.exe file is.

---

### Post by Brownedwg89 on 2006-08-22
is steam.exe in a different folder than C:\program files\steam?

---

### Post by Wafflesomd on 2006-08-22
the actual full directory is wafflesomd\c\program files\steam

---

### Post by Kilz on 2006-08-22
> **Wafflesomd said:**
> the actual full directory is wafflesomd\c\program files\steam

Yes but your winecfg has c: set up to that location. /home/username/c/ the setup script dose it for you. So the windows application thinks its looking at c:\program files

---

### Post by Wafflesomd on 2006-08-22
So what exactly do I do then?

---

