---
title: "Audio gone after crashes - edgy"
date: 2006-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Amitola85 on 2006-11-07
I had a few crashes over the last couple days, which may or may not have been fixed by a RAM switch. (still crossing my fingers on that).

After the last crash, I switched the memory, and booted back up.  Now my audio doesn't work.

I've checked alsamixer nothing's muted that shouldn't be (Master, PCM, CD).

I tried restarting alsa (alsa-utils restart) no change.  

The login screen played sounds, but nothing will after login.  When I try to play something the slider scrolls, but at faster than real-time.  Time for the music runs at approximately 2x, as if it were outputting to file or something.  

Checking System->Preferences->Sound shows everything as 'Autodetect'.  Pressing 'Test' pops up a window saying "Testing" but no sound is heard. 
If I change from 'Autodetect' to 'NVidia CK804 - IEC958', I get the same result.  
If I change it to 'NVidia CK804' I get this: 
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.
```
'ALSA' - Same Result
'OSS' - Same Result
'ESD' - "Testing"

These results are the same for both "Sound Events" and "Music and Movies"

On the next tab: "Sounds" Enable software sound mixing is checked.
Play System Sounds is checked. 
Default Sound Card: NVidia CK804

Any Ideas?

---

### Post by Amitola85 on 2006-11-08
So I got a chance to restart, and X froze on the restart, a quick alt-ctrl-bksp fixed that and now the audio works again... go figure...

---

