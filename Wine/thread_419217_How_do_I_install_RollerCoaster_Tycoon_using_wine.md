---
title: "How do I install RollerCoaster Tycoon using wine?"
date: 2007-04-22
forum: Wine
---

### Post by volksolwagen57 on 2007-04-22
i've tried this:
> wine /media/cdrom1/Setup.exe
the terminal seems to "think" for like two seconds and will do nothing but return me to a new terminal command prompt. i've read as much as i could in the tutorials. i'm not sure how to build directories or anything using wine. i simply found this old windows game and i want to play it. i also have an expansion RollerCoaster Tycoon Loopy Landscapes.
could somebody help me? please?
i appreciate it in advance.

---

### Post by adza on 2007-04-30
a couple of things to check... firstly that cdrom1 is the device you are trying to read from, most default to cdrom0

secondly, that your account has permissions to execute from the drive you could sudo chmod u+x /media/cdrom1 for example (check that for syntax errors before trying though

finally, in the winecfg, ensure that your cdrom is showing as a drive letter, then on the advanced options, change the type from automatic to 'cdrom'... 

if all that fails... then  [http://appdb.winehq.org/appview.php?iVersionId=3766&iTestingId=10688](http://appdb.winehq.org/appview.php?iVersionId=3766&iTestingId=10688) for further info.. ensure that you follow the steps correctly :P

---

### Post by santiagoward2000 on 2007-09-05
Hi everyone!
I know it may be a little late, but using wine 0.9.41, all I had to do was inserting the CD, allow the autorun and click on install.

---

### Post by pdlethbridge on 2007-12-21
x

---

