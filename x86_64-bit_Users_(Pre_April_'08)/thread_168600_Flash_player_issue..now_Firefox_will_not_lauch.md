---
title: "Flash player issue..now Firefox will not lauch"
date: 2006-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by sjashton on 2006-04-30
If anyone can help me restore firefox on my Breezy install i would greatly appreiciate it. I am a newbie and only installled Ubuntu 5.10 a couple of days ago but have been trying to install Flash and java on 64bit machine. I followed the instructions available at: [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) but when i got to the bit where i was to test flash (secton 10) Firefox crashed and i dont know how to restore it, the ADSl is definately up as Evolution can pick up emails. Any info on how i can revert/restore would be gratefully recieved.

---

### Post by gerbman on 2006-04-30
[QUOTE=sjashton]If anyone can help me restore firefox on my Breezy install i would greatly appreiciate it. I am a newbie and only installled Ubuntu 5.10 a couple of days ago but have been trying to install Flash and java on 64bit machine. I followed the instructions available at: [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) but when i got to the bit where i was to test flash (secton 10) Firefox crashed and i dont know how to restore it, the ADSl is definately up as Evolution can pick up emails. Any info on how i can revert/restore would be gratefully recieved.[/QUOTE]If you want to completely remove everything for Firefox (including bookmarks, etc), you could do the following:```
sudo apt-get remove firefox
sudo apt-get remove mozilla-firefox
rm -rf ~/.mozilla
```Then reinstall with```
sudo apt-get install firefox
```If you want to back up your .mozilla directory first to save your bookmarks/preferences just do```
cp -R ~/.mozilla ~/where/to/back/up/
```Hope that helps!

---

### Post by sjashton on 2006-04-30
Thanks Gerbman, that worked a treat. I'm going to have another bash at installing flash/java.

---

