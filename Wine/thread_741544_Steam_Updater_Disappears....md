---
title: "Steam Updater Disappears..."
date: 2008-03-31
forum: Wine
---

### Post by RudiePoo on 2008-03-31
I was wondering if anyone could give me a hand with this... I installed Steam and everything seemed to go fine, however, when I went to run Steam the update got to 26% then closed then opened back up again and finished.  But when I go to run Steam again it opens the updater for a second and closes again and nothing happens.... Any help would be much appreciated :)

---

### Post by RudiePoo on 2008-04-05
Anybody have any ideas?....

---

### Post by aoanla on 2008-04-05
You know how there's that comment at the top of this forum about checking the Wine Applications Database if you have problems, first?

Let's see what it says about Steam...

> 
TROUBLESHOOTING
26% Bug Workaround:

Run this from the directory you installed Steam to:

nice -n 19 wine Steam.exe

If that doesn't work try this:

wine steamTmp.exe SelfUpdate "Steam.exe" 14

If all fails try this before the previous command:

rm ClientRegistry.blob



Does that work?

---

### Post by RudiePoo on 2008-04-06
I've already tried that but it didn't work :/

---

