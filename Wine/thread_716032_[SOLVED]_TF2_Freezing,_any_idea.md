---
title: "[SOLVED] TF2 Freezing, any idea?"
date: 2008-03-05
forum: Wine
---

### Post by Thieflock on 2008-03-05
Everything runs like it should but when I load the game, and select my team the game freezes. I made sure that the proper graphics card driver was working with glxinfo | grep direct and the output Rendering: Yes. Any ideas?


Thanks again for the help.

---

### Post by FrozenFox on 2008-03-05
Hrmm, what version of wine are you running? and did you get it from the repositories (apt-get/synaptic without adding extra repositories like from winehq), directly from winehq, dl it from somewhere else, or did you compile it yourself?

wine --version

---

### Post by Thieflock on 2008-03-05
It is the latest version straight from WineHQ

---

### Post by FrozenFox on 2008-03-05
Strange indeed. Are you on 64 bit, by chance? A friend of mine runs tf2 fine on gutsy on 64 bit. Next time she comes on, I'll ask what she did to make it work, if you haven't fixed the problem by then.

In the meantime, we can try some things.. When it freezes, does it take all of X along with it or can you by chance kill it off? Please run it in the terminal and give us the output, if that's possible. If it's not, try running this.. -maybe- it'll save the information before it totally locks up.

logsave ~/Desktop/tf2log.txt wine /path/to/your/tf2/tf2binaryname.exe

---

### Post by Thieflock on 2008-03-05
I can't kill the process through the terminal but I can alt-tab so I can restart when it freezes.

---

### Post by Thieflock on 2008-03-05
Problem solved for anyone else having this issue:

First of all I was running Feisty Fawn, that was the whole mistake right there, install Gutsy (or later?). But if you also need to know how to install TF2 you can follow this tutorial: 

[http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/](http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/)

Also after I had TF2 running decent on Gutsy there were fps stutters during the game that were annoying. To get around this if you also have this problem is run the game in a window. For whatever reason it will run smooth.

---

