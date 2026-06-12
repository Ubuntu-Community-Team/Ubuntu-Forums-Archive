---
title: "Skype and 64-bit BT Headset Blues (was working, stopped)"
date: 2007-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by tighem on 2007-11-07
Started having a problem with Skype under 64-bit Gutsy last night.

Basically skype was working fine until about an hour into a conference call when it decided to stop working.  Actually, snd_bt_scod crashed on me (running high CPU Util and could not kill it). Ever since then, skype will not work with the BT headset. I've tried everything I can think of short of reinstalling Gutsy (which I'm not really in the mood to do).

Skype now will send 3 chirps to the headset when the call starts, and that's it. I'm using gbtsco to connect the headset (and bluez-btsco on the backend).

Any ideas are greatly appreciated.

---

### Post by tighem on 2007-11-07
Well I just got it work again by disabling the audio service under the bluetooth applet and reinstalling btsco and gbtsco.

I'd love an explanation as to why the "audio" service breaks this but I'm happy for now. Haven't tried rebooting yet, though.

---

### Post by tighem on 2007-11-07
Reboot it did not survive. I'd say this was hit or miss. Totally not stable.

---

