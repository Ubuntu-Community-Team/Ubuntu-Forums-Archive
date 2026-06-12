---
title: "Half life 2 and wine, extra commands at start?"
date: 2008-04-11
forum: Wine
---

### Post by sudo panda on 2008-04-11
Hello all!
Just a quick question.
I was wondering how would i go about making wine do some extra things before starting a game.
I want Half Life 2 to start without steam, so I'm trying to tell it to do the following parameters


  "-steamlocal -game hl2" for Half Life 2"
but how do i add that to a shortcut for example? like with the target line in windows. :confused:

---

### Post by Weichpudding on 2008-04-11
Add the parameters just after the command you would use to run the app.

wine hl2.exe -steamlocal -game hl2

This works in terminals as well as in shortcuts.

---

### Post by sudo panda on 2008-04-11
ahh very well then :)

---

