---
title: "Diablo 2 Maphack Wine problem"
date: 2008-07-05
forum: Wine
---

### Post by dserver on 2008-07-05
I've been trying to use the EPlite maphack for Diablo 2 but it's not working 100%. When run in Windows, EPlite brings up a cmd prompt that says "1 process available for injection. Pausing game to inject." or something to that nature, and then it injects. 
However, in Wine it says "1 process available for injection" and then nothing else. Anyone know why it won't inject into Diablo 2 when run with Wine? Any ideas would be helpful.

---

### Post by Yuki_Nagato on 2008-07-05
Maphackers; in MY Diablo 2?

Sorry.  I am unable to get many "lesser known" pieces of software to work with Wine.  In fact, kudos to you for even getting that to work on Wine.  I was not able to.

As for problems?  Could there be a problem with the registry?  I think that is how Windows programs talk to one another.

---

### Post by dserver on 2008-07-06
I think you might be on to something. I don't know much about registry's, but the maphack as an .exe file and a .dll file. Would a .dll file have something to do with it not injecting correctly?

---

### Post by dserver on 2008-07-06
I found something else out. Before I was using 
```
wine "EasyLoad.exe"
```
to run the exe file, which yielded the "1 process found" but no injection message like the Windows counterpart. However, now I use
```
wine start EasyLoad.exe
```
which yields
```
fixme:exec:SHELL_execute flags ignored: 0x00000500
err:wineconsole:WCUSER_SetFont wrong font
```
Any ideas what this means? My intuition tells me something is wrong with the fonts. Any idea how I should go about resolving this?

---

### Post by dserver on 2008-07-06
I've copied over all my fonts from Windows into the Wine C:Windows\Fonts folder and here is what I get when I run the maphack
```
~$ wine start "C:\Program Files\maphack\EasyLoad.exe"
fixme:exec:SHELL_execute flags ignored: 0x00000500
jon@jon-laptop:~$ err:wineconsole:WCUSER_SetFont wrong font
err:wineconsole:WCUSER_SetFont wrong font
err:wineconsole:WCUSER_SetFont wrong font
err:wineconsole:WCUSER_SetFont wrong font
err:wineconsole:WCUSER_SetFont wrong font

```

Any ideas on how to fix this? Any input is appreciated.

---

### Post by dserver on 2008-07-06
bump

---

### Post by jkr801 on 2008-07-07
dserver i am having the same problem did you make any headway??

---

### Post by dserver on 2008-07-07
I posted the wine font error in another thread and someone posted a solution but it didn't work so what I'm going to try to do is upgrade from ubuntu 7.10 to 8.04 because I read that Wine handles .exe's differently in 8.04. I'm not sure if it will work but I'll update you when the upgrade is complete. What version of ubuntu are you running?

---

### Post by jkr801 on 2008-07-07
im actually running crossover on a intel mac 10.5.4 and its wine based so i thought the solution would be the same..

---

### Post by dserver on 2008-07-07
Even after updating to 8.04 I still can't run it. I've tried the ```
wineconsole
``` command for both Diablo II.exe and EasyLoad.exe with no avail. On a more positive note, AutoTeleport works so as long as your playing a sorceress, you really don't need a maphack.

---

