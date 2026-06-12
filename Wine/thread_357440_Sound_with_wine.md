---
title: "Sound with wine?"
date: 2007-02-09
forum: Wine
---

### Post by MarkLori on 2007-02-09
I finally got brave (and p.o'd at the drivers that had to be manually installed to rebuild under WinXP) and turned my laptop ( a dell Latitude C640 ) into a 100% Linux machine.  I'm running Edgy and all has been fine.  

I can't seem to get sound to work in Wine (Starcraft loaded and running).  Winecfg shows the imbedded sound card which is working with other apps (sound, vids, etc.).  If I look at the Starcraft sound setup it has everything turned off and is not adjustable.  (Like I have no sound card.)  Anyone else had this problem and figure it out?  

I don't know much about wine, so id I'm being stupid, please overlook it.

Thanks,
Mark

---

### Post by Sqwishy on 2007-02-09
you need to fondle with stuff. I had the same problem and i can't remember how i fixed it. When you goto audio tab in winecfg, does it show alsa? or just oss.

---

### Post by Mongoose on 2007-02-10
> **MarkLori said:**
> 
I can't seem to get sound to work in Wine (Starcraft loaded and running).  Winecfg shows the imbedded sound card which is working with other apps (sound, vids, etc.).  If I look at the Starcraft sound setup it has everything turned off and is not adjustable.  (Like I have no sound card.)  Anyone else had this problem and figure it out?  


Go to the audio tab and set the drop down to emulation, enable driver emulation, and you likely want to go to the program tabs and set starcraft to win95 profile.  There should be dozens of HOWTOs for this game if you look.   I use Wine mostly for oblivion and morrowind.

---

### Post by MarkLori on 2007-02-10
Thanks for the replies.  Winecfg only shows OSS not ALSA.  I have driver emulation checked.  I've actually read a bunch of how-to's on this, which is how I got this far.  I tried changing to Win95 emulation but that did not change anything. 

Thanks for the suggestions so far, still looking for more...

---

### Post by MarkLori on 2007-02-11
I found out the ALSA service was not running.  I started it and then selected it in wincfg.   Unfortunately nothing changed.  Still hoping for another good suggestion.

Thanks
Mark

---

### Post by th3rmos on 2007-08-30
I seem to be experiencing the same issue as stated above. When I launch winecfg from the konsole, and click on the "Audio" Tab I see the following errors display inside the konsole window. I am running Kubuntu Fiesty

```
laptop@kubuntu-laptop:~$ winecfg
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
/bin/sh: /usr/bin/esd: not found
```

---

