---
title: "plz help: Guitar Hero III via wine (or virtualbox)"
date: 2007-12-25
forum: Wine
---

### Post by LinuxPS2 on 2007-12-25
Hey, so I just got Guitar Hero III for PC and went to install it on my System 76 laptop, the usual, until i went to run the installer, i keep getting 
> wine: could not load L"D:\\setup.exe": Module not found

Some have suggested to change directory then  just do wine setup.exe that also returned the same error...

I also cannot get my guitar to work, i have followed the guide here --> [http://ubuntuforums.org/showthread.php?t=596347&highlight=guitar+hero](http://ubuntuforums.org/showthread.php?t=596347&highlight=guitar+hero)

and the lights no longer just flash... two flash when i first plug it in but after that there is nothing... any help would be amazing, i think i can figure out the guitar problems but as for installing the game not so much, oh i have also installed it in vitrualbox and i get the error that it is not designed for the version of windows that i am running and i need to upgrade (my virtual machine is an XP install)

---

### Post by cogadh on 2007-12-25
There is a Wine subforum here now for asking any and all Wine related questions. You should post any future questions there. The mods will likely move this over to it once they see it:
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

I don't know anything about your guitar problem, but the error you are getting on the install should be easy to fix. All you should need to do is put in the CD, then run this:
```
wine /media/cdrom/setup.exe
```
Make sure you get the name of the install executable right. Remember that letter case counts, i.e. Setup.exe is different from setup.exe which is different from SETUP.exe which is different from SETUP.EXE... you get the point.

---

### Post by LinuxPS2 on 2008-02-03
yes yes, i have done that - now i get an error that the CD is not in the drive - i get this error even when doing 
> sudo wine '/media/cdrom0/setup.exe'
it seems to have copied several of the files before it comes up with this error... 
anyone know what might be going on?

---

