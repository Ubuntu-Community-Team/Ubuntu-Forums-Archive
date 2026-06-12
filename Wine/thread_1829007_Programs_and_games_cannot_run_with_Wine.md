---
title: "Programs and games cannot run with Wine"
date: 2011-08-20
forum: Wine
---

### Post by tingxyu1996 on 2011-08-20
Hello and I am new Ubuntu user! I got a problem about Wine.

After  I installed a Windows game with Wine. I can't run it! I double click  the game/software or run through the wine(At the top of the screen  Applications > Wine), nothing comes out. 

Anyone who can help me please? Thank you!

Here's the video that what I'm asking about: 
Youtube: [http://www.youtube.com/watch?v=2UomoboxmAU](http://www.youtube.com/watch?v=2UomoboxmAU)

---

### Post by kyletstrand on 2011-08-20
Try opening it from the terminal and see what errors you are getting.

```
wine [file path for CS]
```

 [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3507) lists a few instances of this and it may be of some help also.

---

### Post by kyletstrand on 2011-08-20
Also, have you tried any other programs using wine? Do they give similar results?

---

### Post by tingxyu1996 on 2011-08-20
> **kyletstrand said:**
> Also, have you tried any other programs using wine? Do they give similar results?
Yea... But... I installed in other hard disk, not drive_c. Is another partition. Does it matter?

---

### Post by raja.genupula on 2011-08-20
i heard all windows games are not supported in wine . for specially games use playonlinux .
try it .

---

### Post by tingxyu1996 on 2011-08-20
> **raja.genupula said:**
> i heard all windows games are not supported in wine . for specially games use playonlinux .
try it .
Okay, _[**let's watch this video**]("http://www.youtube.com/watch?v=cVWY7v4HqBs&feature=related")_... Wine can support many games and softwares, after watch the video, _**[watch this too.]("http://appdb.winehq.org/")**_

---

### Post by kyletstrand on 2011-08-20
> **tingxyu1996 said:**
> Yea... But... I installed in other hard disk, not drive_c. Is another partition. Does it matter?
 
Possibly.  I've only ever installed inside drive_c and honestly, I've never had any problems with programs running.  I've had to tweak programs to run efficiently, but never what you're experiencing.
 
Also, maybe you installed the game under the root.  The wine appdb listed this as a potential reason for this.
 
try putting sudo infront of your wine command and see what happens.

---

### Post by raja.genupula on 2011-08-20
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)


goto that link there you can find

---

### Post by tingxyu1996 on 2011-08-21
Okay I fixed the problem! I can play Counter Strike 1.6 and run Any DVD converter Pro now!
The main reason is:
I haven't download and install Windows .dll files and some stuff like vC++ redist... 

Anyway, thank you for spending time to help me solve the problem! Cheers. ;)

---

### Post by realzippy on 2011-08-21
...so you might set thread as solved. (Threadtools)

---

