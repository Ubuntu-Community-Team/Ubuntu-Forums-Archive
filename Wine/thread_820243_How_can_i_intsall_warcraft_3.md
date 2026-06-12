---
title: "How can i intsall warcraft 3?"
date: 2008-06-06
forum: Wine
---

### Post by keylog on 2008-06-06
i have tried install warcraft on ubuntu 8.04 with wine bu i couldn't do..
error massage is

```
setup is unable to read the following data file. your warcraft 3 cd may net have been in the cdrom drive.
setupdat\setup.vis
error 0x00000002: file not found
(c:\temp\020606lockit\installer\source\script.cpp:78)

operation aborted.
```

but my disc was in drive. i have tried that from console and it said that:
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
```
and it opens a window it contains first code..

---

### Post by 4th guy on 2008-06-06
Warcraft 3 installs fine when you use [www.playonlinux.com](www.playonlinux.com)

---

### Post by keylog on 2008-06-06
> **4th guy said:**
> Warcraft 3 installs fine when you use [www.playonlinux.com](www.playonlinux.com)

i have install playonlinux but i can't install warcraft :S

---

### Post by 4th guy on 2008-06-06
It should be pretty straight-forward.

Click on install > games > Warcraft 3
install normally

What's the problem you're having?

---

### Post by keylog on 2008-06-06
i couldn't start the install normally :S it says fisrt code in first massage it's my problem bro..

---

### Post by 4th guy on 2008-06-06
Do you have the latest wine installed?
Is the disk clean?

---

### Post by keylog on 2008-06-06
yess i wrote 

sudo apt-get install wine and somethink like that from this forum..

i found my problem is "http://ubuntuforums.org/showthread.php?t=662116" like it.

---

### Post by 4th guy on 2008-06-07
Are you absolutaly *sure* apt-get points to the wine in the official repository or the one [here]("http://www.winehq.org/site/download-deb")?
Did you download [PlayOnLinux]("http://www.playonlinux.com/en/download.html")? I'm sorry I have to ask again, but it doesn't seem that you've downloaded it.
What version of Ubuntu are you using anyway?

---

### Post by keylog on 2008-06-09
> **4th guy said:**
> Are you absolutaly *sure* apt-get points to the wine in the official repository or the one [here]("http://www.winehq.org/site/download-deb")?
Did you download [PlayOnLinux]("http://www.playonlinux.com/en/download.html")? I'm sorry I have to ask again, but it doesn't seem that you've downloaded it.
What version of Ubuntu are you using anyway?

yesss i have already installed them and i'm using the ubuntu 8.04 and my problem was [PreloaderPageZeroProblem]("http://http://wiki.winehq.org/PreloaderPageZeroProblem")then i have solved it but now my new problem is
```
keylog@keylog-laptop:/home$ cd ..
keylog@keylog-laptop:/$ cd media
keylog@keylog-laptop:/media$ cd cdrom0
keylog@keylog-laptop:/media/cdrom0$ wine install.exe
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
keylog@keylog-laptop:/media/cdrom0$ 

```
it's appear when i try to install warcraft :S
what can i do?

---

### Post by 4th guy on 2008-06-09
Open playonlinux

Applications > Games > PlayOnLinux or Applications > PlayOnLinux > PlayOnLinux

Click on the big install button

Select games from the side menu and type warcraft in the search box.

Click on Warcraft III and click on the Apply button

Point the program to your cd (cdrom0 in your case) and click on next.

That *should* work.

---

### Post by keylog on 2008-06-09
i have tried it but it says again same thing [IMG]http://lh5.ggpht.com/masterkeylog/SE0oNbtuemI/AAAAAAAAB10/1DIlU1PC7Uo/s800/Screenshot.png[/IMG]

---

### Post by Kosimo on 2008-06-09
Did you try installing the latest warcraft III update?

---

### Post by keylog on 2008-06-09
:S i haven't install the warcraft how can i update it :S are you kidding?

---

### Post by Kosimo on 2008-06-09
> **keylog said:**
> :S i haven't install the warcraft how can i update it :S are you kidding?

Sorry, that was my mistake... I though you couldn't run it.  By the way, did you try installing Wine by this (Warcraft 3 dedicated repository?)

Is a specifit Wine Build made by "shae" that should work out of the box.
You can give it a try.

[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=313](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=313)

---

### Post by keylog on 2008-06-09
i have tried it but it's not associeted with my problem..

---

### Post by 4th guy on 2008-06-09
Are you sure the CD is readable? Are there any scratches / dirt on it?

---

### Post by keylog on 2008-06-09
it's working on xp :)

---

### Post by 4th guy on 2008-06-09
This honestly has me stumped. I can not think of anything else.

---

