---
title: "[SOLVED] [B]wierd sound problem[/B]"
date: 2008-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by zorro26 on 2008-02-15
I have just installed new ubuntu gusty 64bit, and having a problem with ma sound,
no sound when i start my system or play audio cd. but i do get sound when i play same cd on Kaffeine. also no sound  when i watch youtube. i got USB speakers? any idea why is that?

kal@kal:~$ ls -l /proc/asound
total 0
dr-xr-xr-x 6 root root 0 2008-02-15 17:27 card0
dr-xr-xr-x 3 root root 0 2008-02-15 17:27 card1
-r--r--r-- 1 root root 0 2008-02-15 17:27 cards
lrwxrwxrwx 1 root root 5 2008-02-15 17:27 default -> card1
-r--r--r-- 1 root root 0 2008-02-15 17:27 devices
-r--r--r-- 1 root root 0 2008-02-15 17:27 hwdep
-r--r--r-- 1 root root 0 2008-02-15 17:27 modules
dr-xr-xr-x 2 root root 0 2008-02-15 17:27 oss
-r--r--r-- 1 root root 0 2008-02-15 17:27 pcm
dr-xr-xr-x 2 root root 0 2008-02-15 17:27 seq
lrwxrwxrwx 1 root root 5 2008-02-15 17:27 SI7012 -> card0
-r--r--r-- 1 root root 0 2008-02-15 17:27 timers
-r--r--r-- 1 root root 0 2008-02-15 17:27 version
 
Can some one pls reply

---

### Post by zorro26 on 2008-02-15
kal@kal:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Audio       ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Some please

---

### Post by xeth_delta on 2008-02-15
Since you have sound in Kaffeine, I would say it is a problem with the sound configuration in Gnome. You moight want to have a look there. I am sorry I cannot offer much help on that, but I use KDE.

---

### Post by zorro26 on 2008-02-15
Still not working very wierd, i have just installed new alsa driver, but no joy. how do i configure gnome.... still no sound on startedup, or any other program but cd or mp3 plays fine with kaffeine.  all control in alsamixer are unmuted and fine .......why is that?:(

---

### Post by xeth_delta on 2008-02-15
> **zorro26 said:**
> Still not working very wierd, i have just installed new alsa driver, but no joy. how do i configure gnome.... still no sound on startedup, or any other program but cd or mp3 plays fine with kaffeine.  all control in alsamixer are unmuted and fine .......why is that?:(

Try restarting alsa:
```
sudo /etc/init.d/alsa-utils restart
```
or
```
sudo /etc/init.d/alsasound restart
```

---

### Post by zorro26 on 2008-02-15
tried that and rebooted my system, its same. no sound anywhere other then kaffeine

---

### Post by xeth_delta on 2008-02-15
> **zorro26 said:**
> tried that and rebooted my system, its same. no sound anywhere other then kaffeine

I can only suggest one more thing for now. Backup /etc/init.d/alsa-utils, /etc/modprobe.d/alsa-base.
Run:
```
sudo alsaconf
```
Follow the instructions.
If it does not work, hopefully someone more knowledgeable than me will come along and help :)

---

### Post by xeth_delta on 2008-02-15
You may also want to look at: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by zorro26 on 2008-02-15
i have already looked at that post and for alsaconfg

sudo: alsaconf: command not found

---

### Post by xeth_delta on 2008-02-15
Give asoundconf a try, and otherwise download the alsa utilities from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download), unpack (tar -xjf file_name.tar.bz2), enter the directory, configure (./configure), compile (make) and install (make install).

Don't remove the directory. You will need it, if you want to uninstall what you just installed (sudo make uninstall).

[EDIT] sudo precedes make install

---

### Post by zorro26 on 2008-02-15
checking for libasound headers version >= 1.0.15... not present.
configure: error: Sufficiently new version of libasound not found.

where do i get that now, i have checked it in synaptic manager and i got one installedi think version 1.0.14

---

### Post by xeth_delta on 2008-02-15
> **zorro26 said:**
> checking for libasound headers version >= 1.0.15... not present.
configure: error: Sufficiently new version of libasound not found.

where do i get that now, i have checked it in synaptic manager and i got one installedi think version 1.0.14

You are missing the headers. Install libasound2-dev.

---

### Post by zorro26 on 2008-02-15
i have just installed it but i am gettin same error masg, i think its looking for version 1.0.15 but what i got is 1.0.15, libasound2-dev that is

---

### Post by xeth_delta on 2008-02-15
> **zorro26 said:**
> i have just installed it but i am gettin same error masg, i think its looking for version 1.0.15 but what i got is 1.0.15, libasound2-dev that is

Does it need 1.0.15? Ok, you can get that from the alsawebsite. Follow the link I gave you earlier. Look for libraries. Same installation procedures, ./configure, make, sudo make install.

---

### Post by zorro26 on 2008-02-15
i reinstalled ubuntu again, and when i was playin round i selected USB as my default device under sound and it worked. thankyou for you help and time

---

### Post by xeth_delta on 2008-02-15
Good to know it woks, but just out curiousity, is your sound card a USB based one?

---

### Post by zorro26 on 2008-02-15
its not realy a sound card, its just usb speakers.... they work fine now. but not my sound card wont work,lol... i am using my TV as second moniter, so when i download stuff i can watch it on TV and dont have to go through converting and stuff, but i got audio wires conected aswell and they not workin. i have to search for that now...lol

---

