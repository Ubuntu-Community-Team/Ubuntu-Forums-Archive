---
title: "Sound test error"
date: 2008-10-19
forum: x86 64-bit Users
---

### Post by Auron_Strife on 2008-10-19
Hi i'm new to Linux using Ubuntu 8.04 LTS 64-bit, spent an hour getting my nvidia 9800 gt driver to work, and now I get a pretty strange message for my sound card.  I have a Creative SB X-FI sound card.  When I go to System-Preferences-sound it is set to AutoDetect, and when I click Test I get the following message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

I re-installed to see if I had messed something up getting my video drivers to work but I still get that message.

Any and all help is greatly Appreciated,

Auron

---

### Post by Auron_Strife on 2008-10-19
Also, not sure if it helps, I got Amarok and when I try to play the "Amarok 1.4 Welcome"  I get the message:

Audio output unavailable; the device is busy.
xine parameters:

---

### Post by nss0000 on 2008-10-19
I think that sound-card is not supported by UBUNTU.

---

### Post by Yellow Pasque on 2008-10-19
See: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Auron_Strife on 2008-10-20
I went through the OSS guide and didn't have any problems until the last command  SUDO make install

near the end it gives me this:

sync
soundoff && sync && soundon
OSS not loaded.

 
Happy i'm not getting that first message now though :P :popcorn:

---

### Post by Yellow Pasque on 2008-10-20
The "OSS not loaded" message always appears at the end of the build, even if OSS has loaded. :? I take it that sound is still not working?

What flavor of X-fi do you own?

---

### Post by Auron_Strife on 2008-10-20
I have the Creative SB X FI ExtremeGamer

What it does now is act like its playing, there is just no actual sound lol.  Maybe a conflict between my sound card and the onboard sound?  Tested my speakers in both and didn't get a sound from either.

---

