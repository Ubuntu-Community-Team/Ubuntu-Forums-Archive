---
title: "[SOLVED] Black screen on WoW start up."
date: 2008-09-02
forum: Wine
---

### Post by Rammatamago on 2008-09-02
Hello,
I have been having a problem when I start World of Warcraft where the login screen is pitch black. I just switched to Ubuntu a few days ago, and am pretty new to most stuff. Right now I'm running Ubuntu 8.04 Hardy. I have a ATI 3850HD with the proprietary drivers.

I tried a few fixes for WoW problems, such as changing the Config.wtf for openGL, editing regedit, turning off all visual effects, and updating wine from 1.0 to 1.1.3. None of which has helped with the black screen.

Any suggestions by chance?

---

### Post by Oldsoldier2003 on 2008-09-02
Moved from ABT to Wine.

---

### Post by Rammatamago on 2008-09-02
Solution found! :D

I just added the three lines below to my Config.wtf, changed the DPI in winecfg to 125, and it's working great so far.

SET ffxDeath "0"
SET ffxGlow "0"
SET gxApi "opengl"

---

### Post by Oldsoldier2003 on 2008-09-02
great news. would you mind marking the thread as solved using "thread tools" so tha it can help others when searching?

---

### Post by Rammatamago on 2008-09-02
> **Oldsoldier2003 said:**
> great news. would you mind marking the thread as solved using "thread tools" so tha it can help others when searching?
Done. Thanks for telling me to do that. New to the forums if it's not obvious. :)

---

### Post by Furen on 2009-05-06
Thank you so much for this solution. It fixed my problem perfectly.

So glad to see working fixes out there in the great sea of questions.

---

### Post by runaway on 2009-05-06
Nice fix I'll use this as well :).

---

### Post by dzong on 2010-05-20
sorry I changed everything that is written, 
ie the 3 lines to change in config.wtf but 
the game is nothing but a black screen is not 
know what to do.

---

