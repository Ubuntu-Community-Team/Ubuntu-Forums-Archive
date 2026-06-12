---
title: "Please insert the correct cd"
date: 2008-11-01
forum: Wine
---

### Post by squirrelplayingtag on 2008-11-01
A class I'm taking using a textbook on cd that doesn't work with linux so I tried using wine to open it up. Everything installs fine but when I try to run it I get an error that says "Please insert the correct cd-rom, select ok and restart the application." when the cd rom is in the drive. In the wine config there is an entry for cdrom0 and is selected as cd-rom under the advanced tab. I also tried copying the cd contents on to my harddrive and making an entry for that folder and setting it as cdrom but that didn't work either. 

dave@dave-laptop:~$ ls -la ~/.wine/dosdevices/
total 8
drwxr-xr-x 2 dave dave 4096 2008-11-01 21:49 .
drwxr-xr-x 4 dave dave 4096 2008-11-01 21:50 ..
lrwxrwxrwx 1 dave dave   10 2008-11-01 21:47 c: -> ../drive_c
lrwxrwxrwx 1 dave dave   13 2008-11-01 21:49 d: -> /media/cdrom0
lrwxrwxrwx 1 dave dave    9 2008-11-01 21:47 d:: -> /dev/scd0
lrwxrwxrwx 1 dave dave    1 2008-11-01 21:47 z: -> /
dave@dave-laptop:~$ wine --version
wine-1.1.7

---

### Post by cogadh on 2008-11-01
The software probably uses some kind of copy protection check that Wine doesn't support. SecuROM is really the only one that Wine does support and it doesn't always support it well.

---

### Post by squirrelplayingtag on 2008-11-01
I don't like the sound of that. Are there any work arounds? I tried searching google but I've only found to use a no-cd crack but theres no crack for this.

---

### Post by cogadh on 2008-11-02
A crack is the only real work-around for copy protection check problems, at least until Wine develops further to support more copy protection functions. Of course, there are certain copy protection schemes, such as TAGES and StarForce, that Wine will never support, since they utilize Windows-based drivers to accomplish their task.

That being said, I was only guessing that a copy protection check is the problem. It might help if you run the application from the terminal then post the output that Wine produces here. That output will often contain error messages that may point to a solution other than copy protection problems.

---

