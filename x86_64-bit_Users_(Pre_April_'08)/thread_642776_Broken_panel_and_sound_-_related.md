---
title: "Broken panel and sound - related?"
date: 2007-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by drfox on 2007-12-17
I was successfully running Gutsy 64 bit, but flash wasn't working. 
Through Synaptic, I installed flash, and when it still didn't work, I installed some codecs and Mplayer.
Still didn't work...I rebooted, and now I get no sound and most of the icons are gone from the panels, which are totally grey, and the grey areas are frozen--I can't right or left-click on them. The 3 icons left on the panels--trash, connection and search are working.
I added a user (didn't know how to add a sudoer) and that user's panels are working, but the sound icon has a red x on it, and I get a warning that I either don't have the sound hardware or the proper gstream isn't/aren't installed.
Alsamixer won't start, and neither does gnome-settings-daemon.
Is there a system log that shows what software I have most recently installed? Maybe I can remove it and get back to work?
Any other suggestions?

Thanks.

---

### Post by azbarcea on 2007-12-18
**1. 'sudo' user**

> **drfox said:**
> 
I added a user (didn't know how to add a sudoer) and that user's panels are working, but the sound icon has a red x on it, and I get a warning that I either don't have the sound hardware or the proper gstream isn't/aren't installed.


**To add a user:** ```
 $ sudo adduser a_username 
```
**To add a user to admin group:** ```
 $ sudo adduser a_username admin
```

Now you have a user with sudo rights.

**2. sound issue**
 I whould do somthing like:
```

$ sudo apt-get purge alsa
$ sudo apt-get install alsa

```
 But I made some research for you:
 *. [http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)
 *. [http://ubuntuforums.org/showthread.php?t=57074](http://ubuntuforums.org/showthread.php?t=57074)

**3. Flash on ubuntu 64**
 Follow this: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by drfox on 2007-12-18
Thanks. I had reinstalled Gutsy 64 before I got your reply. 
I ran the GetFlash script and it didn't break anything, but it also didn't install Flash. I've posted over at the link, and I'll see what their answer is.

Larry

---

### Post by azbarcea on 2007-12-18
> **drfox said:**
> Thanks. I had reinstalled Gutsy 64 before I got your reply. 
I ran the GetFlash script and it didn't break anything, but it also didn't install Flash. I've posted over at the link, and I'll see what their answer is.

Larry

I posted a response there for you ... and you may close this thread if you do not need it anymore :-)

---

