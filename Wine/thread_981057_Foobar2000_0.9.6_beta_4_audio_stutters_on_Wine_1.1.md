---
title: "Foobar2000 0.9.6 beta 4 audio stutters on Wine 1.1.8"
date: 2008-11-13
forum: Wine
---

### Post by Ultimusbuntu on 2008-11-13
Hello,

I have Foobar2000 0.9.6 beta 4 installed through Wine 1.1.8 and the audio stutters even though I have tried following this advice:

"The beta version of foobar2000 uses Directsound by default, which can cause some problems when playing music. In order to get the program to play music properly, you must set the Hardware Acceleration to emulate Directsound. Go to a terimal and type in "winecfg". A window will open with options for you to modify. Click on the Audio tab, and then look for "Hardware Acceleration". It is currently on "Full". Click on it, and you will have a list of options. Click on "Emulation", and then click on "Apply". foobar2000 should now be able to play music. Note that this will make foobar2000 version 0.8.3 give out an error when you try to play an audio file. Just change it back to "Full" in winecfg when you're done using foobar2000 version 0.9 beta."

My Hardware Acceleration is set to Emulation like adviced there and driver emulation is also checked, though that doesn't seem to have any effect. Both ALSA driver and OSS driver are also checked. My soundcard is an onboard Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) with Realtek 880 OSS if that tells anything.


Any ideas? Thanks.

---

### Post by Ultimusbuntu on 2008-11-19
Bump.

---

### Post by karth on 2008-11-19
In case you didn't know, ALSA output is currently broken for the latest wine builds

[http://ubuntuforums.org/showthread.php?t=968179](http://ubuntuforums.org/showthread.php?t=968179)

Either go through OSS only, or downgrade to a previous wine build, or wait for a new version to come out (which should come out pretty soon)

---

