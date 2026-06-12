---
title: "On reboot won't open desktop enviro"
date: 2009-03-14
forum: x86 64-bit Users
---

### Post by Jphenow on 2009-03-14
Whenever I boot I have been getting a variety of things happening, I've been doing minor troubleshooting mind you. One thing is I get an error saying that it'll have to boot in Low-Gaphics mode because type1 module does not exist. I can also get a similar error saying there is a screen specified but not correctly. I have used a few different tools to create new xorg.conf files that doesn't change much. Another error I can get is it going to console and hanging on "*Checking Batter state..." My last common error is it tries to do a resolution of either 1024x768 then 1280x1056 I think it is, then it just drops to console. Only changes I've been making is xorg.conf file by automatically generating them and installing nvidia drivers. Keep in mind this is a fairly fresh install. I've installed it and did one set of updates and on restart this all started happening. Anyone got any clues for me?? Please I've been spending about 2 days on this and haven't gotten much to work with.

Thanks in advance

---

### Post by Kevbert on 2009-03-14
When you installed Kubuntu did you burn your own live CD ? It looks like it may have been corrupted and had faulty files.  Did you [[COLOR="Red"]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded ISO ? Did you [COLOR="Red"][burn]("https://help.ubuntu.com/community/BurningIsoHowto")[/COLOR] at a slow speed (2x best) ?  Have you integrity checked the CD from the CD boot menu ?
Have you run memtest from the CD boot menu ? It's possible that you have faulty memory (windows may seem to work with faulty memory, but may crash occasionally for no apparent reason). You should run memtest for at least two passes. Any problems mean that either the memory is bad, poorly fitted, suspect memory sockets or a build up of dust (which may become conductive over time).
What are you system specs ? (RAM, display adapter, wireless card).

---

### Post by Jphenow on 2009-03-14
I'll try re-writing the disc at a very slow speed. and maybe try a reinstall for the last time. I never had any troubles of this sort on my old 32-bit Ubuntu and my window$ has never crashed on me. I have a:
5600 AMD 2.8 GHz
8500GT GeForce Graphics card
4 slots for RAM but only three filled (a 2 gig, and 2 1 gigs)
 and yes I checked it is built to use memory that's not in pairs
I'll do a memtest and let you know what happens, then try reburning the disc

---

### Post by Jphenow on 2009-03-14
I passed the memory tests and currently the "Low Graphics Mode error" says

> Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

PS I have seen the GUI. I saw them up until I restarted after the first batch of updates. And I've tried opening the roll-back kernel and that doesn't do much for me. If I get a chance to try a new install on a slow burn I'll post results.

---

### Post by Jphenow on 2009-03-14
Okay. Progress has been made. I installed 180.11 Nvidia driver through the console. Then I did sh for the 180.29 I believe it is. Now I can see KDE and KDM which is good. Only problem is that I can't get a resolution above 640x480, and I have a 19" widescreen sooo 1440x900 would definitely be ideal. Any clues?? 

Thanks in advance all

---

