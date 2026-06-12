---
title: "possible ALSA error message with wine"
date: 2007-08-26
forum: Wine
---

### Post by wog on 2007-08-26
I changed the sound setting to ALSA like the FAQ for this forum area says, and now I get an error message when I do winecfg. It says:

james@linux-box:~$ winecfg
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet


What does this mean and is there anything I can do about this without programming skills?

---

### Post by cogadh on 2007-08-26
"fixme" messages are just Wine developer notes. There is really nothing you can do to fix most of them, since they are just there to remind the developers to work on adding support for that particular function.

---

### Post by wog on 2007-08-27
Is ALSA a younger project than OSS? I can't figure out why ALSA would generate all these errors when OSS doesn't seem to.

---

### Post by cogadh on 2007-08-27
Since OSS doesn't get much active development and the ALSA project is fast becoming the Linux standard, ALSA support in Wine was made a project for the Google Summer of Code this year. There has been significant progress made on increasing its functionality in Wine. It is currently about 90% complete, while the OSS support in Wine is about 95% complete.

---

