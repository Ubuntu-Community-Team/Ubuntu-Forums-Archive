---
title: "totem-xine no sound (ubuntu 8.04)"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by RRosset on 2008-05-05
I've been reading for 1 day searching solutions to my problems but none worked for me yet.

I've got 3 players actually, Totem-GStream, Totem-Xine and VLC.
Totem GStream plays video and sound but no menus
Totem Xine plays video and menus but no sound
VLC plays video but no sound nor menus

I'm kinda lost, i installed libdvdcss2 i followed [this guide]("http://ubuntuforums.org/showthread.php?t=611841&highlight=totem+xine+sound") and nothing yet. Usually i haven't got problems with movies. But I bought a dvd (Queen on Fire Live at the Bowl) and... after 00:54 secs the player (totem gstream) restart once. And after a couple of seconds it hangs. Since TotemG doesn't allow me to navigate through menus i can't play anything. TotemXine works like a charm! BUUUUUUT no with no sound. I mean, i can navigate through menus without problem. But the sound is MIA. I select ALL the outputs, (double clickin' on the speaker in the top Ubuntu Bar) and changed the volumes while playing a video saying, maybe xine use a different output. But yet no luck at all :( Plus! if you help me with this, MAYBE my gf would love me a bit more instead of asking why i'm using linux. (haha, this is just a funny comment, but yes, she asked me why, but i simply dont mind, also her father asked me the same, damn M$ world).

SO, this is not all about get laid with someone! it's just I wanna see my dvd!!! I paid for it! hhahaha. Anyways, honestly, any help would be appreciated.

Thanks in advance.

Bob

---

### Post by phlembob on 2008-05-05
I'm a bit new but if you go to system, then administration, then update manager.  You will find a list in sound with most set to auto.  You can change that list to your hardware configuration.  Run test to make sure you get sound.  That may take care of the problem.  No Promises.:guitar:

---

### Post by RRosset on 2008-05-05
Update Manager?!?!

---

### Post by RRosset on 2008-05-05
Ok, none of the players work with this DVD. I tried a few more, SMPlayer is the better option for the moment. I have menus, audio compatibility and video too. As the other players, it skips some menus by default, but at least it lemme choose audio and subs and scenes and needed stuff, so... for the moment this band aid does the trick.
But i'm still trying to find a solution. Maybe if I could change the audio output to the totem xine... but it's not an option in the preferences window. Anyways...

---

### Post by Knight Palatine on 2008-05-05
I had no sound at all. I went into System -> Preferences -> Sound and changed the settings from Autodetect to Alsa-mixer. That seems to work.

Hardy supposedly uses Pulse Audio by default. With Pulse Audio set, however, I get no sound from any of the "Test" buttons in the Sound Preferences dialog. I'm using a M-Audio Revolution 7.1 sound card, BTW.

---

