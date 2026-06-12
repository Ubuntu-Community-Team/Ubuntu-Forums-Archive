---
title: "Using alsa instead of oss as sound server"
date: 2009-06-17
forum: x86 64-bit Users
---

### Post by daedalusman on 2009-06-17
I just installed 9.04 last night and right now oss is the only sound server that will produce sound. I want to be able to use alsa so that I can have multiple programs accessing the sound server at a time. Right now if rhythmbox is open no other programs can access the sound server. Can anyone help me solve this problem? Thanks for any help and let me know if you need more information.

---

### Post by jocko on 2009-06-18
Alsa and oss are not sound servers, they are kernel components, and both are capable of playing sound from multiple sources (but the sound have to be routed through a software mixer or sound server unless you have a sound card with hardware mixer and drivers that supports it).

The default sound server in ubuntu is pulseaudio, and by default it mixes all sounds and passes them on to alsa (or oss if alsa is not available). Just make sure you set all applications to use pulseaudio, not alsa or oss. If one application is using alsa, no other applications will be able to access alsa, so pulseaudio should be the only application that has direct access to alsa.

But, if alsa is missing from the available sound systems you can choose, there must be something wrong with alsa on your system. In that case pulseaudio should be able to use oss, but you probably need to try to find out what's wrong with alsa and fix that to be able to get good quality sound.

If you by some reason don't want to use pulseaudio, alsa has it's own sofware mixer plugin (dmix) that you can activate, but it's quality is not as good as a properly configured pulseaudio.

---

### Post by Yellow Pasque on 2009-06-19
There are lots of guides on ALSA/Pulse troubleshooting, and even a script to build the latest version of ALSA from source. Try those first:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

As a last resort, you should try OSS4 (it uses a virtual mixer, so you can have multiple sounds playing).
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
I'd recommend trying it out in a test environment first and making sure that it works for your hardware. Some users have reported that they were unable to revert back to ALSA/Pulse, even when ALSA gave them sound before they switched.

---

