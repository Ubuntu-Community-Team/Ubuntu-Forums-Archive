---
title: "64bit NIGHTMARE!!!"
date: 2008-05-21
forum: x86 64-bit Users
---

### Post by FluckVista on 2008-05-21
hi first off im uber noob. anyways i installed 64 bit and installed opera just messing around with linux. and the performance compared to windows thus far is great. my problem though is no audio. i couldnt get flash to work in  opera so i used firefox....it WORKS!! but no sound?? so i went to preferences then to sound and was tweaking around. ALC883 Analog, ALSA, and OSS all work when i test them but dont give sound when trying to watch a video in youtube. i select pulse audio from what i hear is what needs to be used in the 64 bit edition and i have no audio at all...not even when i hit test button. Im really interested in linux but without even having my sound working and searching the internet for ever to get a simple thing like flash to work i am very discouraged. i followed the directions for flash 9 above and have read that i will never be able to use flash in opera which is fine but like i was saying i have video now working in firefox but cannot get any sound. if ne one has any comments i would appreciate them greatly.....

also when in myspace the standard music bar that plays music doesn't even appear at all nor play music....just white box

thanks for reading my novel...if you got anything please share!!

---

### Post by Sef on 2008-05-21
A) > i couldnt get flash to work in opera

Flash works in Opera (with sound.)

B) > i installed 64 bit and installed opera

1) Did you install the 64-bit Opera?

2) What version of Opera did you install?

C) > but no sound??

What are your system specs, including sound card?

D) > i followed the directions for flash 9 above and have read that i will never be able to use flash in opera

False.  See A.

---

### Post by soxs on 2008-05-21
> **FluckVista said:**
> hi first off im uber noob. anyways i installed 64 bit and installed opera just messing around with linux. and the performance compared to windows thus far is great. my problem though is no audio. i couldnt get flash to work in  opera so i used firefox....it WORKS!! but no sound?? 
Maybe this helps [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
Note: Flashplayer does _not_ support proper pulseaudioautput, only th beta 10 does.
> 
so i went to preferences then to sound and was tweaking around. ALC883 Analog, ALSA, and OSS all work when i test them but dont give sound when trying to watch a video in youtube. i select pulse audio from what i hear is what needs to be used in the 64 bit edition and i have no audio at all...not even when i hit test button.
You are free to choose whether to use alsa/osss/pulseaudio, there is no limitation due to 64 or 32 bit. It's just the standard.
>  Im really interested in linux but without even having my sound working and searching the internet for ever to get a simple thing like flash to work i am very discouraged. i followed the directions for flash 9 above and have read that i will never be able to use flash in opera which is fine but like i was saying i have video now working in firefox but cannot get any sound. if ne one has any comments i would appreciate them greatly.....

also when in myspace the standard music bar that plays music doesn't even appear at all nor play music....just white box

thanks for reading my novel...if you got anything please share!!

How did you install flashplugin?
Try purgeing it first sudo ```
apt-get remove --purge flashplugin-nonfree
``` and reinstall it with ```
apt-get install flashplugin-nonfree
```
this may help in certain sitautions.

---

### Post by Sef on 2008-05-21
> How did you install flashplugin?
Try purgeing it first sudo
Code:

apt-get remove --purge flashplugin-nonfree

and reinstall it with
Code:

apt-get install flashplugin-nonfree



Since the op has a 64-bit system that will not work.  [Kliz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490") needs to be used to make it work.

---

### Post by soxs on 2008-05-21
No, this command will install nspluginwrapper by default aswell and ontop flashplugin from adobe. In the case it will not work, Kilz tutrial is usefull, but I never required it to make flash work.
Errr: I am sorry, I overread **op** so you're completly right... Kilz tutorial is required.

---

### Post by FluckVista on 2008-05-21
thanks everyone....nothing is working though and my head is pounding!! I think im just going to go back to the 32 bit edition which is supported better and get past this. thanks for everything!

---

### Post by Kilz on 2008-05-21
> **FluckVista said:**
> thanks everyone....nothing is working though and my head is pounding!! I think im just going to go back to the 32 bit edition which is supported better and get past this. thanks for everything!

They have told you exactly where to go to get the information, 32bit is not "supported better". You have made a whole 2 posts, both in the wrong place, and ignored the stickies.

---

### Post by fsckedagain on 2008-05-21
Yeah, what Kilz said...

I have been messing with NVidia driver issues (Quadro FX360M), flash issues (I too, am trying to run 64bit), sound issues in Hardy (volume levels totally horked, either LOUD or soft), and KDE4.

I have followed the stickies and some sage advice from people and have everything except my sound issues worked out and can tell you exactly what I did to fix them.

If you want to play, you have to pay by reading the friggin docs and stickies, that's why they are there.

---

### Post by soxs on 2008-05-22
maybe you should keep an eye on that thread: [http://ubuntuforums.org/showthread.php?t=688707](http://ubuntuforums.org/showthread.php?t=688707)

---

