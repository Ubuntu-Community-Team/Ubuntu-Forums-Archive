---
title: "Mic not working 64-bit Jaunty"
date: 2009-07-02
forum: x86 64-bit Users
---

### Post by arashiko28 on 2009-07-02
The weird part of all this is that it used to work on the 3 previous installations including the last one that was Jaunty 32-bit, then I realized this was a 64-bit capable laptop and reinstalled to try it out, I had everything going perfectly, but I didn't realized that the microphone it's not working, neither the surround speaker.

I have a lenovo Ideapad Y530 running Jaunty 64-bit, my sound configuration is:

> :~$ cat /etc/modprobe.d/alsa-base 
# autoloader aliases 
install sound-slot-0 /sbin/modprobe snd-card-0 
install sound-slot-1 /sbin/modprobe snd-card-1 
install sound-slot-2 /sbin/modprobe snd-card-2 
install sound-slot-3 /sbin/modprobe snd-card-3 
install sound-slot-4 /sbin/modprobe snd-card-4 
install sound-slot-5 /sbin/modprobe snd-card-5 
install sound-slot-6 /sbin/modprobe snd-card-6 
install sound-slot-7 /sbin/modprobe snd-card-7 

# Cause optional modules to be loaded above generic modules 
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; } 
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; } 
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; } 
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; } 
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; } 
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; } 
# Cause optional modules to be loaded above sound card driver modules 
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; } 
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; } 

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway) 
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; } 

# Load snd-seq for devices that don't have hardware midi; 
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for 
#   non-Creative Labs PCI hardware 
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; } 
# Prevent abnormal drivers from grabbing index 0 
options bt87x index=-2 
options cx88_alsa index=-2 
options saa7134-alsa index=-2 
options snd-atiixp-modem index=-2 
options snd-intel8x0m index=-2 
options snd-via82xx-modem index=-2 
options snd-usb-audio index=-2 
options snd-usb-usx2y index=-2 
options snd-usb-caiaq index=-2 
# Ubuntu #62691, enable MPU for snd-cmipci 
options snd-cmipci mpu_port=0x330 fm_port=0x388 
# Keep snd-pcsp from beeing loaded as first soundcard 
options snd-pcsp index=-2 
[COLOR="Red"]options snd-hda-intel model=lenovo-ms7195-dig[/COLOR]

The red line it's the most important and the one that fixes the sound problems at out of the box installation.

The mic does capture sound, but doesn't record it. Ie: Using the sound recorder, I hear myself amplified as if it were a true microphone, but when playing the recording, there's nothing, completely mute... It's hard to expalin, but it's how it is.

---

### Post by arashiko28 on 2009-07-03
**[color="red"][size="7"]bump[/size][/color]**

---

### Post by arashiko28 on 2009-07-07
Please Help!!!

---

### Post by rabdoel on 2009-07-10
same problem here , running a intel quad q8300, and can not get the mic to work on skype innitialy , then tried gnome-soun-recorder and it does not record.

I have now managed to kind of getting the mic to work in skype? test call does recording . but gnome sound recorder still does not record.

---

### Post by rabdoel on 2009-07-10
Ok lookin through the forums I found one person advising to remove pulse and install esound
[COLOR=DarkGreen]
ps -A | grep pulse to  find the process id 
[/COLOR]then

[COLOR=DarkGreen]kill (process id of pulse)[/COLOR]

[COLOR=Black]then remove pulse

[COLOR=DarkGreen]sudo apt-get install remove pulseaudio[/COLOR]

install esound

[COLOR=DarkGreen]sudo apt-get install esound[/COLOR]

remove pulse directory 

[COLOR=DarkGreen]sudo  rm /etc/X11/Xsession/70pulseaudio[/COLOR]
[/COLOR]

this worked here at work on my ubuntu 9.04 32 bit machine without a problem . tested skype and gnome-sound-recorder and this worked fine.

I will try it at home using my ubuntu 64 bit 9.04 and see if this fixes the problem.

---

### Post by marshmallow1304 on 2009-07-10
I had a similar issue.  Try this:

Go to Volume Control, click on Preferences and make sure Input Source is checked.  Then go to the Options tab and set the input source to the correct device.

---

### Post by arashiko28 on 2009-07-10
My problem it's a bit more complicate, the thing is that used to work on 32bit with the exact same configuration.
Now, changing through a list of drivers, I've managed to fix surround speaker, but still no mic...

---

### Post by rabdoel on 2009-07-11
ok the workarround I advised worked for my friends 32 bit eeebuntu and for my work machine that is running 9.04 32 bit.
 
I tried it on my 64 bit 9.04 and it worked for one call. after which it stopped working again in skype. I can now record using gnome-sound-recorder. with no problems.
 
Any guru's out there that can help us ?
 
:confused:

---

### Post by k3m1c4l on 2009-07-27
> **marshmallow1304 said:**
> I had a similar issue.  Try this:

Go to Volume Control, click on Preferences and make sure Input Source is checked.  Then go to the Options tab and set the input source to the correct device.

Actually this may work a little better.... Go to volume control, preferences and make sure "capture" is checked. This should get your mic working and I have tested it in gnome sound recorder

As far as skype is concerned, skype static oss works for me. 


HP dv7 1372cl
64 bit ubuntu 9.04

---

### Post by arashiko28 on 2009-08-07
Nope, it was selected from the beginning and still nothing. I've just decided to wait for 9.10 and go back to 32-bit version. Even though I admit 64-bit works better, has many program compatibility issues.

---

### Post by Arup on 2009-08-08
For issues with Skype, removing Pulse and install OSS and then remove regular Skype and install OSS Skype, it works out very well.

Instructions for installing OSS at [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by arashiko28 on 2009-08-22
I don't have skype, the problem is general with the mic. But thanks anyway.

---

### Post by ken78724 on 2009-08-24
Marshmallow, erased > **marshmallow1304 said:**
> Volume Control

---

### Post by ken78724 on 2009-08-24
new Skype download no affect

---

### Post by ken78724 on 2009-09-04
unclear which OSS4 instruction in [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound). to use to get sound or make mic work

---

### Post by ken78724 on 2009-09-05
if you have a car that runs do not fix it

---

