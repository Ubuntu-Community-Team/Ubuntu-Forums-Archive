---
title: "Firefox download function broken"
date: 2005-07-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by optikshell on 2005-07-23
any time I click a link that would let me download something (i.e open the download manager), all that happens is a new window opens with nothing in it.  Sometimes it'll just act like its loading something, but then stops.  Never opens the download manager.  

It did this 2 days ago, so I re-installed Firefox, restarted Gnome, and it worked again.  Now, when i try to do that... nothing works.  Even re-installing doesn't help.  

Please help, thanks for any advice.

---

### Post by optikshell on 2005-07-23
wow... this is really starting to suck...

every time i want to download something, I have to re-install firefox, then restart Gnome... help please  :?

---

### Post by filterban on 2005-07-23
What version of FireFox?

Tamir has a binary for 1.0.6 that might work better; I believe he said 1.0.5 wasnt' working all that well.  Also, many of us have had problems with "deerpark" versions.

---

### Post by optikshell on 2005-07-23
1.0.2  ... i think I have a sucky repository list... anyone care to post an extensive one?

---

### Post by jowaxman on 2005-07-25
[QUOTE=optikshell]any time I click a link that would let me download something (i.e open the download manager), all that happens is a new window opens with nothing in it.  Sometimes it'll just act like its loading something, but then stops.  Never opens the download manager.  

It did this 2 days ago, so I re-installed Firefox, restarted Gnome, and it worked again.  Now, when i try to do that... nothing works.  Even re-installing doesn't help.  

Please help, thanks for any advice.[/QUOTE]
 I am also having this problem.  It's quite maddening.  Has anyone solved this problem?

---

### Post by Pse on 2005-07-26
I was having that same problem until I installed 1.0.6. There should be a version in the official reps right now =)

---

### Post by Jet2k5 on 2005-07-26
Just incase some of you guys are still having trouble please remove or uncomment backports from your **/etc/apt/sources.list**, and then remove firefox.  After you have removed firefox download it again by either going into synaptic and getting it from there.  


Also for some reason downloading firefox doesn't download the *mozilla-firefox-gnome-support* package.  You can either go back into synaptic and get it or just type in after the commands on top.  So in the end it should all look like this :
```
sudo apt-get update && sudo apt-get remove mozilla-firefox && sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support
```

---

### Post by eolo999 on 2005-07-26
[QUOTE=jowaxman]I am also having this problem.  It's quite maddening.  Has anyone solved this problem?[/QUOTE]
 I have the same problem. I "solved" right clicking on the download link and selecting "save destination as".
It's quite comfortble waiting for new releases.

---

