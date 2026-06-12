---
title: "Wine blockes audio device"
date: 2008-04-26
forum: Wine
---

### Post by presston on 2008-04-26
I have a problem. When i run applications in wine, no other application have access to audio devices.
Testing audio properties in this time give me message:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resourse is busy or deny.

how to fix that?

---

### Post by schtufbox on 2008-04-26
Which sound driver is wine using? OSS?

---

### Post by presston on 2008-04-26
alsa oss. sound - ad 1985

---

### Post by schtufbox on 2008-04-26
by that I'm guessing wine is set to use oss, but you're loading it with aoss so it's piped through ALSA?
Personally I just have wine set to use alsa and it works fine, bit of a change from about 2 years ago that's for sure.

---

### Post by mriedel on 2008-04-26
On hardy, select OSS in wine and run wine as "padsp wine". This runs wine in a pulse audio wrapper that emulates oss.

[http://ubuntuforums.org/showthread.php?p=4798919#post4798919](http://ubuntuforums.org/showthread.php?p=4798919#post4798919)

---

### Post by presston on 2008-04-26
may anybody make screenshot of your wine audio settings?

---

### Post by presston on 2008-04-26
up. while "winecfg" in terminal i have:

> presston@X2:~$ winecfg
ALSA lib conf.c:1592:(snd_config_load1) :3:1:Unexpected }
ALSA lib conf.c:2849:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration
err:wave:ALSA_DefaultDevices snd_config_update() failed:  Invalid argument(-22)
ALSA lib conf.c:1592:(snd_config_load1) :3:1:Unexpected }
ALSA lib conf.c:2849:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration
ALSA lib conf.c:1592:(snd_config_load1) :3:1:Unexpected }
ALSA lib conf.c:2849:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2713:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3076:(snd_config_update_r) hooks failed, removing configuration



---
after a lot of search in different forums i guess, that problem is in non-multiple audio setting. that's why there is no sound in more then one application :( but i have not find right resolve for this problem (many of them are in forums, but no one helps me).

----
Aloso i have found that alsa do not work at all, only oss (& oss mixer)

---

### Post by presston on 2008-04-26
please, move this topic to "Multimedia & Video"

---

