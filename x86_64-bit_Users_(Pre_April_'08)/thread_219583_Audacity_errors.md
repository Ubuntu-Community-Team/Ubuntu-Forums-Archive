---
title: "Audacity errors"
date: 2006-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by yourearthlymaster on 2006-07-20
Hi all.  when I try to run audacity I get this message at startup of program:  


Error Initializing Audio
     There was an error initializing the audio i/o layer.  
     You will not be able to play or record audio.  

Any help would be greatly apprieciated.  thanx.

---

### Post by timetunnel on 2006-07-20
Close all other audio-aware applications (Rhythmbox, Xine, MPlayer, whatever) before starting Audacity. At least on my system Audacity only works when no other application is running that uses the sound system.

---

### Post by DeadEyes on 2006-07-20
try runnning:
**killall esd**
before launching Audacity

---

### Post by timetunnel on 2006-07-20
> **DeadEyes said:**
> try runnning:
**killall esd**
before launching Audacity

Isn't that the way it used to be in Breezy? On my system (Dapper) it's not neccassary to kill esd.

---

### Post by Wyrm_1972 on 2006-07-20
Go to System->Preferences->Sound and disable ESD software mixing.

You can try wrapping it with 'esddsp audacity' in terminal, but this made everything play at half-speed on my P3 550... might be okay on a faster machine (let me know). You may need to 'sudo apt-get install esound-clients' to get esddsp

---

### Post by DeadEyes on 2006-07-20
> **timetunnel said:**
> Isn't that the way it used to be in Breezy? On my system (Dapper) it's not neccassary to kill esd.
yes probably, I had to do it in Breezy, I can't remember if I've ever had to do it in Dapper.

---

