---
title: "Sound Problem"
date: 2006-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Flipper on 2006-02-19
Hi, I removed my ibook clamshell's battery and Breezy booted to login normally, and when i entered my username/password it went to a brown blank screen..

I searched in the forum and i found out that the problem was related to the date of the system cause it was reset to jan 1 , 1900.. so i pressed Ctrl+alt+F1 and changed the date with the date --set command, startx and wverything was nice and clean again except for the sound :| 

The problem is:

I can hear the sounds ( so it isnt hardware ) but when i open the sound icon (near the clock) i get an error that says:

"Registry is not present or it is corrupted, plase update it by running gst-register"

Can anyone help me? do i have to re-install any package or something?

---

### Post by Flipper on 2006-02-19
Solved! reiinstalled the GSfilters and everything is fine now

---

### Post by jdp on 2006-02-19
For future readers, it should be noted that iBooks don't have a PRAM battery to retain clock settings when the main battery is removed withouth the AC plugged in.  THere is a small capacitor that can keep the settings for up to 20 seconds to provide time to swap main batteries.  Also, later G4s also have this setup.

---

