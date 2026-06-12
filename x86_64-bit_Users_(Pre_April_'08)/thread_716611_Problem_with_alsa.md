---
title: "Problem with alsa"
date: 2008-03-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Benjamin_Vedder on 2008-03-06
Hello.

I have an intel HDA sound card and use the optical port for my logitech z5500 speakers. One day it suddenly didnt work anymore. I dont know why, but the analog output did still work, and it had nothing to do with the mixerchannels. I reinstalled the new alsa driver, lib and utils like described in this howto: 

ttps://help.ubuntu.com/community/HdaIntelSoundHowto

and ALMOST got it working. The problem is that SOME applications cant use alsa, like cedega. Cedega tells me alsa isnt installed. Its the same thing with quake4, i have to use oss output for sound in quake4 because alsa gives no sound. I can still play games like that, but i cant have mp3 running at the same time, and thats a problem. Also, every time i reboot the computer, all the mixerchannels are muted, they dont remember the settings.

Most applications still work with alsa, like vlc, mplayer, amarok, quake3.... so, can it be something with the permissions maybe? and if so, what could it be? Thanks for replies.

---

### Post by LoneWolfJack on 2008-03-06
If cedega comes with a config tool like WINE, go to the audio tab and disable ALSA in favour of OSS. Fixed all ALSA issues for me in WINE.

---

### Post by Benjamin_Vedder on 2008-03-06
Thats what im doing right now, but that still doesnt let me listen to mp3 while playing games.. i dont use cedega that much, but anyway, it feels better to have the sound working correctly.

btw, the problem with the mixerchannels muting themselves every time i reboot is annoying, is there some way ti fix that?

---

### Post by Yellow Pasque on 2008-03-09
These scripts seem to work well for people:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

