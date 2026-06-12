---
title: "2 problems"
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Psychoslim on 2007-12-04
when i click my update manager i get this error

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package j2re1.4 needs to be reinstalled, but I can't find an archive for it.'



when i go to my system/admin/synaptic package manager i get this error

E: The package j2re1.4 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


I am useing Ubuntu amd 64 i have both firefox and firefox 32 along with swiftweasle and swiftweasle 32. I noticed these errors when i got them from here [http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)  The 3in 1 terminal program. 

i have been trying to work on these for the past 3 hours and still i could do nothing but ask for help.

I am so lost on what to do and try and really do not want to continue for i am almost dead sleepy.

Will be back on later in the day for help and advise. Thank you.
:confused::confused::confused::confused::confused:

---

### Post by Kilz on 2007-12-04
You might want to do these commands to see if it will help.
```

sudo apt-get install -f
sudo apt-get clean
```

Now, are you are aware that Blackdown has no security manager? That running it will allow applets to do anything a applet running on your computer to do like reformat your drive, and install files (maybe a rootkit) ? Are you sure you want to run this security risk?

---

### Post by Psychoslim on 2007-12-04
psychoslim@psychoslim-laptop:~$ sudo apt-get install -f
[sudo] password for psychoslim:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package j2re1.4 needs to be reinstalled, but I can't find an archive for it.
psychoslim@psychoslim-laptop:~$ sudo apt-get clean
psychoslim@psychoslim-laptop:~$ 

thats what happen with the code.

2: you lost me man.

---

### Post by Psychoslim on 2007-12-04
i am getting close to reinstalling the OS again.

---

### Post by saru411 on 2007-12-04
> **Psychoslim said:**
> 

2: you lost me man.

he means that the java blackdown that you installed is a security risk! im unsure of how or why you have it installed. you should have installed a 32 bit borwser using kilz script here([http://ubuntuforums.org/showthread.php?t=202537&highlight=java](http://ubuntuforums.org/showthread.php?t=202537&highlight=java)). you most likely tried installing many other javas through synaptic and finally found kilz script. when you install things and they dont work, you should uninstall them. leaving unused programs on your pc is sloppy.

---

### Post by Psychoslim on 2007-12-04
so i should basicaly redo the computer again and start again?

i really do not know how to uninstall anything on this system. 

>newb< thats what i am LOL

---

