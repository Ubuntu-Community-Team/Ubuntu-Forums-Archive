---
title: "Wine/Steam load callback error please read!"
date: 2007-09-24
forum: Wine
---

### Post by mikeym on 2007-09-24
I'm trying to get hl2 running with steam.

I had it running perfectly last night after I compiled the CVS for it but this morning steam is coming up with a strange error and I can't find a solution to it online. 

Steam starts as per normal, logs in then opens up the main window, but the web content doesn't load (it stays white) and the terminal output counts shutdown up to 300 then gives the message:

"client callback thread error"

```

dir: C:\Program Files\Steam\ *.mix
dir: C:\Program Files\Steam\ *.asi
dir: C:\Program Files\Steam\ *.flt
Shutting down. . .
300client callback thread error

```

It appears to be a problem with gecko (steam website?) but I've tried reinstalling gecko and typing the following works:


```
wine iexplore http://www.winehq.org

```

Any thoughts?

---

### Post by mikeym on 2007-09-24
I posted this as a bug on *winehq* and I got directed to another bug [here]("http://bugs.winehq.org/show_bug.cgi?id=9733") (mine was a duplicate - I hadn't found theirs).

Is there anything I can do, or do I just wait until it gets fixed in the CVS? 

They mention patches but I take it that's just to the CVS.

P.S.

I found a way of bypassing the bug. Launch steam with the *-silent* option then right click on the taskbar icon as soon as it appears and select games.

You can then launch your game exe directly with options from [here]("http://developer.valvesoftware.com/wiki/Steam_Command_Line_Options#Command-line_parameters").

Well assuming you are running something from valve.

---

### Post by mikeym on 2007-09-24
The patches have been set in the latest CVS so the problem is fixed.

---

