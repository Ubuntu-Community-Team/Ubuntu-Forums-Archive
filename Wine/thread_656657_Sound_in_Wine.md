---
title: "Sound in Wine"
date: 2008-01-02
forum: Wine
---

### Post by pdusen on 2008-01-02
I've got 2 applications running under Wine: Reason, for audio production, and Steam, for gaming. I have wine set to using ALSA. Here are the Wave Out devices listed in the Wine configuration under ALSA:

[LIST]
[*]dmix:0
[*]dmix:1,FORMAT=S32_LE
[/LIST]

(EDIT: My Wine version is now 0.9.52, after a poster below suggested I update)

When I first started Reason, under audio devices it was using dmix:0, which had no sound. However, I had working sound when I switched it to dmix:1.

Now the problem I'm having is that I can't get any Steam games to play any sound. I'm guessing that, like Reason, they are defaulting to dmix:0. How can I set it so they default to dmix:1?

---

### Post by foolsh on 2008-01-03
I would update to the latest version of wine its up to .9.52 now
It just started acting a whole lot better two releases ago
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
if that doesn't work I'm sorry I couldn't help

---

### Post by carrett on 2008-01-03
If you haven't already, you might also want to fiddle with the audio tab in winecfg.

Good luck...

---

### Post by pdusen on 2008-01-03
> **carrett said:**
> If you haven't already, you might also want to fiddle with the audio tab in winecfg.

Good luck...

In my original post I gave the settings in the audio tab. I just can't figure out how to change the default from dmix:0 to dmix:1.

> **foolsh said:**
> I would update to the latest version of wine its up to .9.52 now
It just started acting a whole lot better two releases ago
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
if that doesn't work I'm sorry I couldn't help

Updated, but didn't change anything... thanks anyway.

Anyone else have any suggestions?

---

### Post by pdusen on 2008-01-03
I've seen some pretty technically apt people on this board; I'm sure somebody out there might have some insight into my problem.

---

### Post by foolsh on 2008-01-04
do you by chance have two sounds cards installed?

---

### Post by pdusen on 2008-01-04
The only sound card I use is my Chaintech, however, various programs detect the HD audio output on my Radeon card as another sound card.

Now that I think about it, my first boot into Ubuntu required me to change some settings to get Alsa to default to the chaintech rather than the HD audio on the Radeon.

...However, this doesn't answer the standing question of how to get Wine to default to dmix:1.

---

### Post by foolsh on 2008-01-04
does anyone know if checking the emulation box on the sound tab in winecfg might have any good/bad results for this person?
or
if linking /dev/dsp to /dev/dsp1 might help or have bad consequences?

---

### Post by pdusen on 2008-01-04
> **foolsh said:**
> does anyone know if checking the emulation box on the sound tab in winecfg might have any good/bad results for this person?
or
if linking /dev/dsp to /dev/dsp1 might help or have bad consequences?

Checking the emulation box made no difference.

What does the second option do?

---

### Post by pdusen on 2008-01-05
Guys, this is a little bit ridiculous. What I'm asking for doesn't *sound* like such a hard thing to do, but apparently it is?

---

### Post by pdusen on 2008-01-07
I've just got this install of 7.10 set up largely the way I like it, and I'd rather not start experimenting too much and accidentally break something beyond my own ability to repair. So I would really appreciate some sort of assistance in this problem.

---

### Post by happyhamster on 2008-01-07
Not sure if I can help, but could you show the output of the following commands:

aplay -l
cat /proc/asound/cards
cat /proc/asound/modules
cat /etc/modprobe.d/alsa-base

---

### Post by pdusen on 2008-01-07
```
patrick@asrock:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AV710 [Chaintech AV-710], device 0: ICE1724 [ICE1724]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: AV710 [Chaintech AV-710], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
patrick@asrock:~$ cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xff2ec000 irq 24
 1 [AV710          ]: ICE1724 - Chaintech AV-710
                      Chaintech AV-710 at 0xdc00, irq 21
patrick@asrock:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_ice1724
patrick@asrock:~$ cat /etc/modprobe.d/alsa-base
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
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
patrick@asrock:~$ 

```

---

### Post by happyhamster on 2008-01-08
- Ok, the most rigorous try is blacklisting the radeon soundcard by blocking the snd-hda-intel module. In a terminal:

sudo nano /etc/modprobe.d/blacklist

- Add the following lines at the end of that file:

# Added by user, jan 2008
blacklist snd_hda_intel

- Save (ctrl-o) en exit the editor (ctrl-x). Next: reboot and check if the module is gone:

cat /proc/asound/cards
cat /proc/asound/modules

- I don't know if your current wine-install will accept such changes without complaining though (check winecfg). Perhaps you need to update wine with the commando:

wineprefixcreate

- Worst case scenario is that you have to re-install wine (although you should try keeping/copying the .wine folder first). Good luck.

---

### Post by happyhamster on 2008-01-08
- BTW, if you do want to keep snd-hda-intel, or if blacklisting causes trouble, than you could try setting the soundcard index for both cards manually:

sudo nano /etc/modprobe.d/alsa-base

- At the end of that file add:

# Added by user, jan 2008
options snd-ice1724 index=0
options snd-hda-intel index=1

- Save (ctrl-o) en exit (ctrl-x). Next: reboot and check if ice1724 has index 0 (index 0 = default card)

cat /proc/asound/modules

- This may result in you having to tweak the sound settings for   other applications though.

---

### Post by pdusen on 2008-01-08
Happyhamster: Thank you very much, I will try your solutions. I don't use the ATI audio for anything in any case.

---

### Post by pdusen on 2008-01-08
It worked perfectly! Thank you very much! :guitar:

---

