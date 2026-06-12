---
title: "Wine text-entering issue"
date: 2008-07-18
forum: Wine
---

### Post by jeffbray on 2008-07-18
Here's my issue:
I'm running Ubuntu 8.04 64-bit with the most updated version of wine. I'm trying to play Everquest (which is a Wine Silver Application). The issue I'm having is that I can't type text into any of the text fields. I can select the text fields (a text field being, to me, the place where you enter your username and password when logging in), but I can't type into them. I thought maybe it just wasn't giving a read-out, but when I try to log-in it tells me I must enter something (implying that nothing was received)

Any idea what this issue could be, or how to fix it? Any help would be nice.

---

### Post by Michael.1 on 2008-09-23
Have the same problem on Ubuntu 8.04.1 and Wine 1.1.5 with latest updates.
Keyboard input work weird, I can only type symbols like /\-= Enter and Tab with appropriate keys. Neither letters nor digits work. Also Shift key has no effect. This situation is in all wine applications, even in Wine Notepad.
But sometimes randomly all the keys start to work fine for a little time and then suddenly stop.
As I remember, it was OK with some older version of wine. I didn't try to force an older version of wine, cause I'm afraid of losing all my wine applications' settings.

-----------
Update: Now the problem is solved. The cause of such keyboard behavior turned to be xneur app. After adding wine to exception list, input works fine in wine apps.
I suggest any keyboard-controlling software can somehow interfere with wine input.

---

