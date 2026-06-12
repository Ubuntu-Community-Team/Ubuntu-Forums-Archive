---
title: "no sound"
date: 2009-04-02
forum: x86 64-bit Users
---

### Post by earthtux on 2009-04-02
Hello guys
after yesterday's synaptic update
i lost my sound
so I followed the troubleshoot steps in this [link](https://help.ubuntu.com/community/SoundTroubleshooting)
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```


```

$ lspci -v | less | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


```

so it seems that my sound card works, just no sound
I also checked the alsamixer
Master and PCM are not muted

anyone can help pls? thx

---

### Post by las.leandro on 2009-04-02
I've also lost my sound since the last update, and my soundcard is working fine too! :(

---

### Post by Hooya on 2009-04-02
I ran across this issue yesterday afternoon on my laptop.  Actually, it was way worse than you guys, alsamixergui wouldn't even run!  For some reason my desktop wasn't affected.  Anyway, I got it fixed by using the script found here:

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Download the "Alsaupgrade..." file, unzip.  Run the script with the -di option.
```
sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh -di
```
from the directory the file is in.  Give the thing time; on my aging laptop it took 20 minutes to fix.  Reboot, had sound back!

---

### Post by earthtux on 2009-04-02
> **Hooya said:**
> I ran across this issue yesterday afternoon on my laptop.  Actually, it was way worse than you guys, alsamixergui wouldn't even run!  For some reason my desktop wasn't affected.  Anyway, I got it fixed by using the script found here:

[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

Download the "Alsaupgrade..." file, unzip.  Run the script with the -di option.
```
sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh -di
```
from the directory the file is in.  Give the thing time; on my aging laptop it took 20 minutes to fix.  Reboot, had sound back!

really appreciate your reply
mine is a X61t laptop 
do you know what happened or what the last update has done to the sound configuration?
btw will this script work if I use pulseaudio as my sound manager?
thx

---

### Post by earthtux on 2009-04-03
I wonder if anyone else lost his sound after the system update
bump!!!

---

### Post by xigen on 2009-04-03
Yes.

I lost sound as well.

My supposition is that it is related to kdelibs and a failed upgrade.

 Depends: kdebase-runtime but it is not going to be installed
  Depends: kdelibs5 (>=4:4.1.96) but 4:4.1.4-0ubuntu1~intrepid1.1 is to be installed

---

### Post by earthtux on 2009-04-05
on my system, those 2 packages works fine after the update........
bump

---

### Post by earthtux on 2009-04-06
just got another system update
still no sound..........
bump

---

### Post by kdmellow on 2009-04-09
I don't know if this issue is similar to what you guys have been experiencing, but my sound had also been working until the last set of updates. Now, sound will play for a while, but if I stream media via firefox then I am no longer able to play audio files on the machine. VLC will show that the audio track is playing, but no sound comes through. 

If I use the Sound Prefernces, the tests will play audio. Occasionaly, closing ff will allow me to play audio / video files with sound. Other times I have to reboot. The other odd piece to this is that Pidgin will still play sounds indicating users signing off / on.

Any thoughts?

---

### Post by earthtux on 2009-04-13
I solved it
I use the alsa update script posted in the forum
and then go to volume control shown
in the picture i attached, pls check the speaker 
wala i got my sound back
hope this helps

---

### Post by las.leandro on 2009-04-13
My sound is fine again! Thx!! :guitar:

---

### Post by Thelatinprodigy on 2009-04-27
Never mind. I got it. Thanks for the link.

---

### Post by EvilRobot on 2009-05-13
I have the same problem, no audio at all after synaptic system update (audio was working before update). 
I've tried the "Alsaupgrade" and it still doesn't appear to have worked. 
I'm running Ubuntu Studio 9.04 64-bit (which was installed from a CD not upgraded from an older version of Ubuntu) on a ThinkPad T61p. Now pulse audio is also installed (I'm not sure if that helps) and the sound device is a Intel HDA AD198x. I did a check following the Sound troubleshooting steps and I noticed it says that pulse audio is running but ESound Daemon and Jack are not could this be part of the problem?
Any help or suggestions would be appreciated.

---

### Post by EvilRobot on 2009-05-14
I was able to fix the no sound issue in Ubuntu Studio 9.04 64-bit by following the steps in this thread _[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)_ under the heading _Reinstalling ALSA_. I'm not sure what's different about uninstalling and reinstalling the alsa drivers this way but I think it might have had something to do with installing the Packages gdm and ubuntu-desktop. Hope this helps any one else who might be having the same problem in Ubuntu Studio.

---

