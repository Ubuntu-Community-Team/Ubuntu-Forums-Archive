---
title: "Corrupted the harddrive - help!"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by TuckWat on 2005-11-18
Hey guys, one day my ibook battery died and it turned off incorrectly.  It restarted asking to do some disk checks and I ran them and I chose some option like overwrite or something ( It was a couple weeks ago).  It now loads up and stops at a brown screen right before logging in.  There is a "Invalid rom signature 7323 should be 0xaa55" message on the console screen before freezing.  I can press ctrl alt del and get to different sessions - is there anything I can do before I reformat?  Thanks guys

---

### Post by seatea on 2005-11-19
This may  be a little like the blind leading the blind as I am new to Linux, but I get the same error message about  the  "invalid rom signature" since I installed Ubuntu  on  a PM G4 400 tower. I have been ignoring it, which may not be  the  right  choice for that occurrence. I have no problem booting and using Ubuntu, however. You might  possibly boot into  rescue mode by typing  rescue at the  boot prompt or, altenatively, boot from a Live  CD of  Ubuntu and enter rescue at the  "boot" prompt. Allegedly there are instructions on what to do  next. I haven't done that task yet and  can't verify what will happen in the rescue mode. There is a help  guide on  the web at [www.linux-mag.com/content/view/2286/](www.linux-mag.com/content/view/2286/) that is a little  complicated, for me  anyway, and has some rather thorough discussions on emergency recovery for Linux. It  is called "The Linux Emergency  Room" and  written by Roderick W. Smith who has written several Linux books. I would try to  explain it, but having  read it and, again not having actually  tried it out, I don't want  to misinform you. Good luck.

---

### Post by er-ku on 2005-11-22
Probably some system files were corrupted (like the kernel, for example). I think i'm having the same ROM signature error too, but I don't think it's relevant. My iBook boots just fine.

---

### Post by ssam on 2005-11-22
it could easily have reset the system clock. see

[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

### Post by Ptero-4 on 2005-11-22
You probably got a system file messed up. The rom signature error is actually a warning that comes up b/c the ubuntu kernel seems to be unable to recognize correctly the rom signature for most ATI cards. This doesn't affect normal X11 operation though.

---

### Post by spade_shark on 2005-11-23
No backup to restore from?  You are out of luck then.  Backup the entire drive / backup needed files.  Before you reinstall, I would suggest you write zeros to the drive with any of the numerous drive utilites.  This will verify the integrity of the drive and will not take long to run.  This step allows the drive to remap (bypass) any faultly sections of the disk that may have developed errors.  Then you can start with a "clean" drive for the new build.

---

