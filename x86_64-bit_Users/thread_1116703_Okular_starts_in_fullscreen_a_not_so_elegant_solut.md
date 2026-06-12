---
title: "Okular starts in fullscreen: a not so elegant solution"
date: 2009-04-05
forum: x86 64-bit Users
---

### Post by aimonas on 2009-04-05
Hello everyone, 

I've been facing a problem with Okular starting in fullscreen mode on 8.10-64bit. There are several references to this problem and the most common cause seems to be an interference with compiz. The corresponding remedy is to go to

1. System-->Preferences-->CompizConfig Settings Manager-->Utility-->Workarounds
and deactivate Legacy Fullscreen support.

However, this didn't work for me, as also with compiz deactivated the problem persisted. Another proposal that I found is to rename the config files (adding for example an arbitrary extension):

2. a)~/.kde/share/config/okularrc (in my case, strangely it was named No Name)
   b)~/.kde/share/config/okularpartrc

This didn't work as well for me.
What did actually work was the change of some parameters in the okularrc file. In specific, I opened the file (if it doesn't open Properties-->Permissions-->Allow executing file as program) and then 

3. Fullscreen=false 

instead of the true value that was there by default. 

Now the problem is solved even with compiz on (having performed solution (1) first). 

Not so elegant and clear solution, but it did the trick for me. Hope it is useful.

Greetings
aimonas

---

### Post by 3Miro on 2009-04-05
On KDE 4.2, you can go to System Settings -> Window Behavior -> Windows Specific, and you can set parameters on how the programs are supposed to star up. Maybe something can be fixed from there.

---

### Post by Calimo on 2009-04-19
I've been looking for a true solution for weeks... and this one works! :D

Thanks a lot aimonas ;)

---

### Post by shvr on 2009-05-08
HI everyone,
  In my case none of these solutions worked. but changing DesktopBackground-> VisualEffects to 'none' (earlier normal) solved the problem.


Cheers
shvr


> **aimonas said:**
> Hello everyone, 

I've been facing a problem with Okular starting in fullscreen mode on 8.10-64bit. There are several references to this problem and the most common cause seems to be an interference with compiz. The corresponding remedy is to go to

1. System-->Preferences-->CompizConfig Settings Manager-->Utility-->Workarounds
and deactivate Legacy Fullscreen support.

However, this didn't work for me, as also with compiz deactivated the problem persisted. Another proposal that I found is to rename the config files (adding for example an arbitrary extension):

2. a)~/.kde/share/config/okularrc (in my case, strangely it was named No Name)
   b)~/.kde/share/config/okularpartrc

This didn't work as well for me.
What did actually work was the change of some parameters in the okularrc file. In specific, I opened the file (if it doesn't open Properties-->Permissions-->Allow executing file as program) and then 

3. Fullscreen=false 

instead of the true value that was there by default. 

Now the problem is solved even with compiz on (having performed solution (1) first). 

Not so elegant and clear solution, but it did the trick for me. Hope it is useful.

Greetings
aimonas

---

### Post by domino1241 on 2009-05-08
Changing the value in ~/.kde/share/config/okularrc to Fullscreen=false did it for me as well.  I don't know why you consider this solution "not so elegant," it is easy to do and works like a charm!  Many thanks.

---

### Post by pvfloripa on 2009-09-07
Hi everyone,

For me, it only worked when I combined solution 1 with solution 3.
Thanks for the help!

---

