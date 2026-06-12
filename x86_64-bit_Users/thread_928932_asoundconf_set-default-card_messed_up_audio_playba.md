---
title: "asoundconf set-default-card messed up audio playback"
date: 2008-09-24
forum: x86 64-bit Users
---

### Post by ATMOS_SKY on 2008-09-24
Updated from command-line like ubuntu updated window suggested and sound doesn't work now.

I ran the command that messed my perfectly working sound up

       **_  "asoundconf set-default-card NVidia"_**

then realized audio-playback wasn't working for anything so tried to run
**"asoundconf reset-default-card"**
and haven't done much else since

I installed pulseaudio and have alsa, 
I'm a semi-noob and have a hp tx1000 tablet

The sound was working perfectly before this, I could record from my webcam's mic (above the screen) and play music and use skype
**but now everything is saying there is "something wrong with the playback"**

let me know if you'd like to know anymore about my system :)

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
out put of     **"asoundconf list"**
Names of available sound cards:
NVidia

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

out put of    ** "aplay -l"**
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

out put of    ** "arecord -l"**
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

out put of    ** "pulseaudio"**
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0"): initialization failed.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

---

### Post by VincenzoAMD64 on 2008-11-19
Hi, I have the same problems on my HPTX1000 with Ubuntu 8.10 just installed. I have already downloaded the last alsa driver, built and installed but nothing happened (also the configuration steps I made for ubuntu 8.04 and previous version).
I think the problem is the kernel version, I am trying to install alsa on the older one 2.6.24-21 because I see it has the same /lib/modules/2.6.24-21-generic/ubuntu/media structure of previous releases.

I will inform you soon
Bye

---

### Post by VincenzoAMD64 on 2008-11-21
No good news, the problem is still present. Someone has an idea or suggestion?

---

### Post by VincenzoAMD64 on 2008-11-22
The problem has been resolved! ; D
This morning the update manager downloaded automatically some upgrades for pulse audio package, I issued a "sudo alsaconfig" command to reconfigure alsa and now I can hear the voice of my little TX1000.

Greetings Vincenzo

---

### Post by Loredrum on 2008-12-02
Ciao vincenzo, ho anche io lo stesso problema, ho installato le ultime versioni dei driver alsa però su ubuntu 8.10 non va, posso chiederti che update hai fatto di preciso?

Lorenzo

---

### Post by VincenzoAMD64 on 2008-12-05
Cattive notizie, il problema sembrava risolto ma alcuni giorni fà l'audio è tornato muto, sto ancora indagando...

---

### Post by VincenzoAMD64 on 2008-12-05
Ok,
here the final solution to have a working audio,
linux distribution:ubuntu 8.10
kernel:2.6.27-8-generic
audio driver:alsa-driver-1.0.18a




Here some configuration settings:

File: /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
fuse
lp
rtc
snd-hwdep
snd-hda-intel
# bcm43xx
b43



File:/etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# added by TouchKit installer
blacklist usbtouchscreen
blacklist touchkitusb



File: /etc/modprobe.conf
options snd-hda-intel model=3stack
options bcm43xx fwpostfix=.v3


Finally check the "Volume Control" panel,
Master, PCM, Front must be ON

Bye Vink

---

