---
title: "PC Speaker wierdness"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by capecove on 2007-06-06
Hello all...

Your friendly neighborhood annoyance here with another question that may seem hilarious to you...

Why does my Thunderbird play an alert tone through my pc speaker when it has completed checking and downloading my mail? My sound is working fine otherwise (I can hear it on startup, shutdown, sound preferences, cd audio, etc.). In fact, nothing makes that pc speaker beep except for Thunderbird and that only after all email is downloaded. 

I know the Thunderbird setting is set to "system new mail sound" and can be changed to a WAV file. Does this mean the system default sound for incoming email is through the pc speaker? I was shocked to hear it actually function. I built my own machine but forgot that I had hooked up the pc speaker. :)

Any ideas? Thanks for the information...

---

### Post by tszanon on 2007-06-12
> **capecove said:**
> Hello all...

Your friendly neighborhood annoyance here with another question that may seem hilarious to you...

Why does my Thunderbird play an alert tone through my pc speaker when it has completed checking and downloading my mail? My sound is working fine otherwise (I can hear it on startup, shutdown, sound preferences, cd audio, etc.). In fact, nothing makes that pc speaker beep except for Thunderbird and that only after all email is downloaded. 

I know the Thunderbird setting is set to "system new mail sound" and can be changed to a WAV file. Does this mean the system default sound for incoming email is through the pc speaker? I was shocked to hear it actually function. I built my own machine but forgot that I had hooked up the pc speaker. :)

Any ideas? Thanks for the information...
I believe it's not only you, but everyone else. Well, me too, at least. :)
But I never tried to change that. I don't even know if thunderbird comes with a custom sound for incoming mail. If I recall correctly, the windows version has a custom sound. Maybe it's just the case of changing this setting you talked about.

---

### Post by david_2001 on 2007-06-12
In Thunderbird, select Edit | Preferences, pick the General tab and then click the Advanced... button opposite Play a sound (see screenshot).  Plays through the sound system on my PC and not through the speaker.  EDIT: Oops, thinks again, Thunderbird uses oss and not alsa for sound, so install alsa-oss if you haven't already and restart.

---

### Post by capecove on 2007-06-12
Thanks for that screenshot. I was able to change the setting. I sure thought it was hilarious to associate the default sound with the PC Speaer considering that there are perhaps more pc's out there with working external speaker/sound card setups than those with working PC speakers. ;) Boy how time changes things.

---

