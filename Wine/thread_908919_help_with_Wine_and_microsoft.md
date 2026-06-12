---
title: "help with Wine and microsoft"
date: 2008-09-02
forum: Wine
---

### Post by nynoah on 2008-09-02
I tried to install Medial player in Wine.  It would not install because it said I did not have a valid version of windows.  Now, I am having something in my computer constantly sending crap off to microsofts IP address.  I know this because MoBlock is telling me.  How can I turn this off and get rid of this?  I don't want Microsoft snooping on me.

N

---

### Post by Oldsoldier2003 on 2008-09-03
Moved to Wine forum and given a free bump.

---

### Post by Liviu-Theodor on 2008-09-03
In [FONT="Courier New"]Applications -> Wine -> Browse C:\ drive[/FONT], just look for the [FONT="Courier New"]Media Player[/FONT] and delete it. If it is not there, it cannot do any harm. You could try also uninstall it, but sometimes you cannot uninstall the easy-way such programs.

---

### Post by lakersforce on 2008-09-03
You could also install Firestarter and block of the ip-adress.

---

### Post by nynoah on 2008-09-03
I have fire starter.  I have uninstalled media player too. I am still having an entity somewhere in my computer that is trying to communicate with microsoft.  I don't want to just block it.  I want it gone.

---

### Post by aoanla on 2008-09-03
Are you sure it's something to do with Wine?
After restarting, /nothing/ should be being run by Wine, so it's a bit puzzling.

Have you tried using netstat and lsof to pin down what the process is?
(Or, looking at the output of ps -efm and seeing what processes are running, for a start.)

---

