---
title: "Help getting wineASIO to run in FLStudio??"
date: 2015-12-23
forum: Wine
---

### Post by nick_robinson2 on 2015-12-23
Not sure if this should be in the Wine forums but..
So I'm running Ubuntu 14.04.3 and for the past month have been trying to get FL Studio 12 to work in it.
I've taken every step on this page [http://forum.image-line.com/viewtopic.php?p=721289](http://forum.image-line.com/viewtopic.php?p=721289) and this video [https://www.youtube.com/watch?v=gjbSaOAdm2Y](https://www.youtube.com/watch?v=gjbSaOAdm2Y)
So far my only problem is that wineASIO isn't working; it shows up as a device in audio settings and says "open" but I'm not getting any sound. The visualizers show that sounds are being made but I'm not hearing anything.
I think the issue is with my sound card; I have an X-Fi Titanium installed as the primary sound card. I get sound in my browser just fine, and in wine when I click "test sound" but I think I may be missing something in regards to wineASIO communicating with it.
I've downloaded all the newest alsa packages.. what am I missing??

---

### Post by howefield on 2015-12-24
Thread moved to the "*Wine*" forum.

Have you browsed the Wine website for that [application]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=178") ?

And an old but apparently solved thread here.. [http://ubuntuforums.org/showthread.php?t=2001698](http://ubuntuforums.org/showthread.php?t=2001698)

---

### Post by yoshii on 2015-12-25
Did you check your settings in Wine Config? (winecfg)?  Also, are you running JACK (before launching FL Studio) or running PulseAudio?  Have you configured Pulse Audio Volume Control  and Mixer device settings?

I am running FL Studio also in Ubuntu Studio v14.04.3 and I implemented some speed tweaks like disabling unneeded services with .override files and by disabling file access time loggin (noatime) in fstab.  I also tried to disable any CPU throttling stuff too.  Unfortunately, I can't get very good performance in FL Studio compared to native Windows users.  I think FL Studio can only use one CPU instead of multiples when in Wine.  When I run some of the demos, I my CPU starts stuttering at 90% even though it's a 3 GHz quad core.  Very frustrating.  Let me know if you get any better results.

---

