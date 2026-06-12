---
title: "New WoW Issue"
date: 2008-08-24
forum: Wine
---

### Post by ChewyNougat on 2008-08-24
This is my wife's laptop. Up til today, it has run Ubuntu/Wine/WoW without any issues. But today she ran the update manager and now WoW will not work. 

I'm not sure what version of wine she had before, but 1.0 seemed to cause the issue (if Wine is the culprit here after all). I downgraded to 0.9.59 in Synaptic, but the issue still happens. The issue is as follows:

Upon starting, WoW will run for 20-30 seconds before having issues. This is regardless of whether I actually log in. So I can start the game and let it sit at the login screen, and you'll begin to see intermittent graphical artifacts that eventually get more dense (over the course of 5-10 seconds). The game will then slow to rendering a frame every 3-4 seconds before finally freezing with lots of pixelated artifacts on the screen. Before it freezes, I can CTRL+ALT+BKSP to avoid a hard reboot. 

If wine is still suspect, what else can I try? If it could be something other than Wine, what would it be?

Thanks in advance.

---

### Post by kdorf on 2008-08-24
You could try deleting or moving your wine prefix and reinstalling.
```
mv ~/.wine ~/.winebackup
```

---

### Post by ChewyNougat on 2008-08-24
I have currently tried:

- Uninstalling wine (moving the .wine to .winebackup) and reinstalling it.
- Doing this with both versions of wine available in the standard repo's (1.0 and 0.9.59).
- Playing with wine's settings, running in a window, different OS, etc. etc.
- Forcing regeneration of Config.wtf in the /wtf folder in WoW (in case it was a WoW setting not playing nice anymore)

No luck so far. Is it possible that an update to some other package earlier today could have caused this? 

Thanks.

---

### Post by ChewyNougat on 2008-08-24
This issue has been solved.

I got the latest graphics driver and installed Wine 1.0 and seems to be working.

---

