---
title: "Sound Card lost"
date: 2007-12-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrbeags on 2007-12-21
Hey all,

I've looked through some other posts, tried troubleshooting but I still can't get my sound card to work.  I tried reinstalling the drivers direct from alsa, but still when I do 

```
aplay -l
```

I get nothing.  I'm using a VIA8237 soundcard.  Thanks!

---

### Post by bford16 on 2007-12-21
I have a similar sound card (maybe even the exact same one).  My Asus A8V-VM motherboard has a VIA soundcard, identified by Ubuntu as a VIA VT82xx or AD198x soundcard.  It works perfectly for me.  The key seems to be adding this line at the end of /etc/modprobe.d/alsa-base.:

options snd-hda-intel position_fix=1 model=3stack

Here's my /etc/modprobe.d/alsa-base.
```
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel position_fix=1 model=3stack
```

---

### Post by mrbeags on 2007-12-21
Tried that, still nothing.  Thanks though.  The output from aplay -l is:

aplay: device_list:205: no soundcards found...


It was working fine until I applied some updates.  I would prefer not to do a clean install, but I think that may be the simplest way to solve it.

---

### Post by mrbeags on 2007-12-22
adding that last line helped after I reinstalled.  I probably messed with something unknown to me the first time that made my graphics card go MIA.  Thanks!

---

