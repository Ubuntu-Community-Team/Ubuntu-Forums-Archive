---
title: "Alsa sound will only play in one program with wine...."
date: 2008-05-06
forum: Wine
---

### Post by Kanaric on 2008-05-06
When Wine is open it hijacks the sound on my computer so that only the first program I run with it will have sound. Anything else outside of wine and inside of wine will not play any sound what so ever.

When wine is not running any other native linux program works fine...

Does anyone have a solution to this?

---

### Post by cogadh on 2008-05-06
If you are using a current version of Ubuntu (not Kubuntu), it isn't actually using ALSA anymore, it uses PulseAudio. You probably need to install the pulseaudio-esound-compat or libasound2-plugins package to allow Wine's ALSA support to correctly interact with PulseAudio.

---

### Post by Kanaric on 2008-05-07
> **cogadh said:**
> If you are using a current version of Ubuntu (not Kubuntu), it isn't actually using ALSA anymore, it uses PulseAudio. You probably need to install the pulseaudio-esound-compat or libasound2-plugins package to allow Wine's ALSA support to correctly interact with PulseAudio.

Unfortunately I am using fedora at the moment on this machine.

---

### Post by Kanaric on 2008-05-07
pulseaudio doesn't even show up as a choice in wine if that is a problem, in my preious install on ubuntu it would of been in there.


NO sound choice in wine config will work when a linux program, such as a mp3 player, is using sound what so ever. I find this to be very strange since I can play multiple native linux sound programs at once.

---

### Post by cogadh on 2008-05-07
On a PulseAudio system, Wine uses ALSA or OSS and communicates with the PulseAudio server through a compatibility plugin. As far as Wine is concerned, it doesn't know or care that the system it is running on uses PulseAudio.

If you are using Fedora 8, then it also uses PulseAudio instead of ALSA and you probably need to install the Fedora equivalent of the packages I mentioned originally. However, its been years since I last used Fedora, so I can't really give you specific instructions on how to take care of that.

---

### Post by Kanaric on 2008-05-07
would I need 32bit versions of both of those files?

---

### Post by cogadh on 2008-05-07
Not sure, I've only used 32-bit myself, never had to try and figure out what to do on a 64-bit system.

---

### Post by Mushed on 2008-05-07
I have the same problem as Kanaric. I have pulse installed and working. It works great with firfox/amorak both running. But when I play wow I can only get sound from it when I open that first. But then I can't run Amorak without it crashing. 
With WoW running the stream is there in the volume control in pulse, but there's no sound. ><

---

### Post by Kanaric on 2008-05-08
> **cogadh said:**
> Not sure, I've only used 32-bit myself, never had to try and figure out what to do on a 64-bit system.

I found the esound compat file and it was already installed but couldn't find that libasound thing, as you said it probably is named something different.


I had a problem in Wine with fedora with Nvidia and I had to download the 32 bit libraries and then it worked great. I can't find or just simply don't know what the sound libraries are called for this... though sound DOES work (unlike the nvidia problem).

> I have the same problem as Kanaric. I have pulse installed and working. It works great with firfox/amorak both running. But when I play wow I can only get sound from it when I open that first. But then I can't run Amorak without it crashing.
With WoW running the stream is there in the volume control in pulse, but there's no sound. ><
What sucks for me, and probably you, as well is that the great majority of all groups that people game with use Ventrilo. In WoW, when I played that, CS, and now Eve-Online I have yet to see someone use something else and if you are using that while playing games you have to get this working... aside the fact that I usually like listening to music, lol.

---

### Post by Kanaric on 2008-05-09
bump

---

### Post by cogadh on 2008-05-09
In a [different thread](http://ubuntuforums.org/showthread.php?t=785567) on a similar topic, [reassuringlyoffensive](http://ubuntuforums.org/member.php?u=314581) reminded me that PulseAudio's ALSA plugin does not work with Wine at all at the moment. There are three patches in the works to correct the issue, but I have no idea when they will be available. If you switch Wine to using OSS instead of ALSA, it might correct some of the problems, unfortunately, I believe Ventrilo won't work with OSS at all. As an extreme options, you could remove PulseAudio completely and then install ALSA.

---

