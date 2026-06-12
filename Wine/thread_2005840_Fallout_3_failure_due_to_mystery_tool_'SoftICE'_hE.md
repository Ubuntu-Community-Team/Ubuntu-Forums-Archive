---
title: "Fallout 3 failure due to mystery tool 'SoftICE' hELP!!"
date: 2012-06-18
forum: Wine
---

### Post by ScratchPuddin on 2012-06-18
So I just got around to installing fallout 3 on ubuntu 12.04. Used the tutorial on winehq, followed every step and thought it would work fine but whenever I try to launch the game I get this error message pop-up:

[I]A required security module cannot be activated.
This program cannot be executed (3000).

Please have a look at [http://www.securom.com/message.asp?m=module&c=3000](http://www.securom.com/message.asp?m=module&c=3000) for further, more detailed information.[/I]

The link brings me to SecuROM's website with a message telling me this:
**[SIZE=2]SecuROM™ has determined that the debugging tool 'SoftICE' is running. Please close 'SoftICE' before you start the application.[/SIZE]**

   I have never heard of such a program and I haven't found mention of a single person having the same problem when trying to play fallout on ubuntu. Any help on how I can deactivate this 'SoftICE' would be greatly appreciated! I just want to kill me some ghouls!!

---

### Post by pbrane on 2012-06-18
SoftICE is a debugging tool. SecurROM seems to think you're running the program in a debugging environment. It sees wine as softICE. Not sure how to fix that. Perhaps the winehq web site has some info on this.

---

### Post by NotSoRandomUsername on 2012-06-18
SoftIce if I remember correctly is a tool to make game cracks. For some reason it thinks that SoftIce is running. Try using a other "Launcher".

---

### Post by pbrane on 2012-06-18
> **NotSoRandomUsername said:**
> SoftIce if I remember correctly is a tool to make game cracks. For some reason it thinks that SoftIce is running. Try using a other "Launcher".

Actually SoftICE is a kernel mode Windows debugger. 

[http://en.wikipedia.org/wiki/SoftICE]("http://en.wikipedia.org/wiki/SoftICE")

---

### Post by ScratchPuddin on 2012-06-18
> **NotSoRandomUsername said:**
> SoftIce if I remember correctly is a tool to make game cracks. For some reason it thinks that SoftIce is running. Try using a other "Launcher".

What sort of other "launcher" could I use? I've also tried installing through .playonlinux but the game still launches with wine.  I own the retail disc version of fallout, so I don't see why it would be wanting to crack

---

### Post by pbrane on 2012-06-18
It may be that SecuROM isn't going to let you start this game in wine. 

One thing to try is changing the windows version to Windows 7 in wine config.

---

### Post by ScratchPuddin on 2012-06-18
Have tried windows 7, xp, and vista to no avail. Thanks for your advice anyway, I'll try and dig deeper

---

### Post by oldos2er on 2012-06-19
Moved to Wine.

---

