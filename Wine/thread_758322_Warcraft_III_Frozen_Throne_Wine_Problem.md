---
title: "Warcraft III: Frozen Throne Wine Problem"
date: 2008-04-17
forum: Wine
---

### Post by zuknivek on 2008-04-17
I just got an older HP computer from a friend that worked fine. Its a good day when you get a free computer. The original OS was windows so immediately i switched to the best OS ever(Ubuntu of course). Doing this i could not get Warcraft III: frozen throne to work. Advanced desktop effects work perfectly. I got desktop cube to work flawlessly and i know the computer meets the requirements to play Warcraft because the kid i got it from played warcraft all the time on it. I never had the Warcraft CD's and on windows I just copied the program files folder of Warcraft over to my computer and it worked by using the Frozen Throne exe file. When i add the application to wine everything works fine. Now when I right click the Frozen Throne exe and open with wine it opens but it looks like this:
[IMG]http://i186.photobucket.com/albums/x303/kevinkuz2009/Screenshot.png[/IMG]
HALP

---

### Post by Stunts on 2008-04-18
Hi!
I'm no expert in this, but here's what I know:
Wine will have issues with desktop effects, so try and disable them before running war3.
You can also try to run with
```
wine war3.exe --opengl
```
Also make sure that you are using the latest update from blizzard (1.21 I think, at least it's what I'm using here) which disables copy protection (I'm 80% positive on this).
Also, what graphics cards do you have?
I had a laptop which had and Intel GL 8045 (or something along those lines) that made Warcraft look similar to what you've shown in the screenshot.
Plus, what version of wine are you using?
It runs very well on 0.9.59 which is what I'm using here. I know some earlyer versions did cause regressions and made the game unplayable.
Good luck, and I hope this was of help!

---

### Post by zuknivek on 2008-04-18
> **Stunts said:**
> Hi!
I'm no expert in this, but here's what I know:
Wine will have issues with desktop effects, so try and disable them before running war3.
You can also try to run with
```
wine war3.exe --opengl
```
Also make sure that you are using the latest update from blizzard (1.21 I think, at least it's what I'm using here) which disables copy protection (I'm 80% positive on this).
Also, what graphics cards do you have?
I had a laptop which had and Intel GL 8045 (or something along those lines) that made Warcraft look similar to what you've shown in the screenshot.
Plus, what version of wine are you using?
It runs very well on 0.9.59 which is what I'm using here. I know some earlyer versions did cause regressions and made the game unplayable.
Good luck, and I hope this was of help!

Ubuntu says that my graphics card is an intel 845. It is crappy integrated stuff though. My wine version is 0.9.59. Disabling the desktop effects did nothing. I signed into battle.net and got the updates and i still can't run the game. I am not sure how to fix the problem but it might be my graphics card after all. Any ideas?

---

### Post by Stunts on 2008-04-18
Well, I never managed to make it run on my old laptop, precisely due to the crappy graphics. I tought it could be the driver that was out of date, but when I tried to change the old driver to the new one my X wouldn't start and I had to restore my xorg.conf manually.
I guess you can try it tough. Make a backup of your xorg.conf first. If you need more assistance I'll be arround for a while.
BTW: Did you try using the --opengl command?
Let me know what you think.

---

### Post by zuknivek on 2008-04-20
> **Stunts said:**
> Well, I never managed to make it run on my old laptop, precisely due to the crappy graphics. I tought it could be the driver that was out of date, but when I tried to change the old driver to the new one my X wouldn't start and I had to restore my xorg.conf manually.
I guess you can try it tough. Make a backup of your xorg.conf first. If you need more assistance I'll be arround for a while.
BTW: Did you try using the --opengl command?
Let me know what you think.

I did the --opengl command and i get this: 
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\war3.exe": Module not found
kevin@kevin-desktop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```

---

### Post by Hairy_Palms on 2008-04-20
yea the exact same problem i had on my old laptop with an intel 845 integrated chip, by the sounds of its a bug with the intel driver

---

### Post by zuknivek on 2008-04-20
Is there any way to solve this problem? I'm lost.

---

### Post by syczu on 2008-04-20
I had some problems when my warcraft 3 was blinking all the time, then I changed resolution and it was OK.

Did you try to run w3 windowed?

---

### Post by zuknivek on 2008-04-23
> **syczu said:**
> I had some problems when my warcraft 3 was blinking all the time, then I changed resolution and it was OK.

Did you try to run w3 windowed?

Nope. I'm not sure how. I will try that though.

---

### Post by janfsd on 2008-04-24
> **zuknivek said:**
> I did the --opengl command and i get this: 
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\war3.exe": Module not found
kevin@kevin-desktop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```
It seems you are not running the command from the folder where warcrafts is. So before running that command, do:
```
 cd path/to/warcraft3
```

---

### Post by coolkid5 on 2008-04-26
Check this thread: [http://ubuntuforums.org/showthread.php?t=768533](http://ubuntuforums.org/showthread.php?t=768533)

---

