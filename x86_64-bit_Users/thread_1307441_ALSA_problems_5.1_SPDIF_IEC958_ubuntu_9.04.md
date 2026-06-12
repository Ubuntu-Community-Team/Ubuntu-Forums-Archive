---
title: "ALSA problems 5.1 SPDIF IEC958 ubuntu 9.04"
date: 2009-10-31
forum: x86 64-bit Users
---

### Post by TimTow on 2009-10-31
Someone please help.  I cannot output anything more than PCM 2.0 through my optical cable from my motherboard.  

for your reference:

aplay -l :

card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0sudo nano /etc/modprobe.d/alsa-base.conf

aplay -L:


front:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

im on a desktop.  Motherboard is an ASUS M2N32 SLI.  I have a dual installation going with ubuntu 9.04 and windows XP.  I only use XP for MATLAB and it would be impossible for that to cause any sort of confliction because the problem persisted long before I applied the dual boot.  Motherboard is 64 bit architecture.  I have tried modifying the .asoundrc and .asoundrc.conf files.  no help.  I have tried modifying the alsa-base.conf file with sudo nano /etc/modprobe.d/alsa-base.conf by adding the card name, specific device, everything I can think of.  I have disabled pulse audio and the ability for any program that naturally tries to use it, and have directed them to ALSA.  but no matter what I do, I can't get

cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1988B

to switch to the digital device.  I have an amp that displays the audio stream being played through it, it always ensures me that PCM 2.0 is the stream it is receiving.  I know there is a way to get 5.1 out of the optical line.  I have tried switching the output from rythymbox, totem, mplayer, vlc, amarok, anything I could think of.  2.0 is all I know!  I have the option under system>preferences>sound for HDA NVidia AD198X Digital selected for all output types, yet the above seems to indicate that I am not using it.  NO 5.1 output.  I apologise if anyone thinks this thread is redundant (I have seen plenty of posts on this subject) but I still haven't found a solution.  I refuse to accept this as an impossibility, and by posting this thread, I hope to find that solution.  Someone please help me stream unaltered sound from my optical line.  anyone, anyone? 

links I have sifted through to get to this point:

[http://www.hardforum.com/showthread.php?t=1102718](http://www.hardforum.com/showthread.php?t=1102718)

[http://ubuntuforums.org/showthread.php?t=1297750](http://ubuntuforums.org/showthread.php?t=1297750)

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

[http://www.alsa-project.org/main/index.php/Asoundrc](http://www.alsa-project.org/main/index.php/Asoundrc)

[http://ubuntuforums.org/showthread.php?t=845317](http://ubuntuforums.org/showthread.php?t=845317)

[http://ubuntulinuxhelp.com/the-simple-way-to-get-51-surround-sound-audio-working-in-ubuntu/](http://ubuntulinuxhelp.com/the-simple-way-to-get-51-surround-sound-audio-working-in-ubuntu/)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=805877](http://ubuntuforums.org/showthread.php?t=805877)


your attention is greatly appreciated

---

