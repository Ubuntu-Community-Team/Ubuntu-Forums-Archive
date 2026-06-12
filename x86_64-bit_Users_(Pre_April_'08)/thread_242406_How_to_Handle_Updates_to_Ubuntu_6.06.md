---
title: "How to Handle Updates to Ubuntu 6.06"
date: 2006-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-08-23
Hi,

I'm somewhat Linux literate, and a former Windows user.

I'm currently using 6.06 on an AMD64 3700. It has taken some work to get things working, and I'm still in the process of getting things the way I want them.

I have built IPTV as well as some other open source applications. In order to view TV with mplayer on my desktop with my PVR-150 I have to do the following after each boot:

[I]sudo rmmod ivtv

sudo modprobe ivtv tuner=50

ivtv-tune -tus-cable -c10 -d /dev/video0

mplayer -vo xv /dev/video0[/I]

1) Is there a way to set this up so that I won't have to do this after each restart? The reason I have to do this is because after boot, ivtv is not recognized, and sometimes there is no tuner recognized.

2) When there are system header updates, I have to rebuild from scratch. Is this normal? Must I rebuild each open source application from scratch dependent on system headers or is there a better way to handle this?

Thanks

---

### Post by srirammurali on 2006-08-23
try creating a shell script from your what you need to do and add it to startup programs, via System -> Preferences -> Sessions -> Startup Programs

---

### Post by killkoy on 2006-08-24
To create the script you need to do the following
sudo gedit
then enter
```
#!/bin/bash
sudo rmmod ivtv
sudo modprobe ivtv tuner=50
ivtv-tune -tus-cable -c10 -d /dev/video0
mplayer -vo xv /dev/video0

```
Then click file > save as and save it in /usr/bin/
then type this command ```
sudo chmod 777 /usr/bin/name-of-file
```
replace name-of-file with the name of the file :p
then add the name-of-file to the startup programs as srirammurali said

---

### Post by bper on 2006-08-24
OK, and thanks.

Too bad I have to have this done every time (at start-up with the script). I thought maybe there could have been some configuration setting that would save the settings from the last configuration rather than configuring each time. I will do this. Thanks a lot for the help.

What about the change to the headers. Would I also have to rebuild all of my open source code every time there are changes to the headers?

Thanks.

---

