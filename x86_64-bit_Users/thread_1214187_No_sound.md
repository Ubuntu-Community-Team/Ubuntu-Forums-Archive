---
title: "No sound"
date: 2009-07-15
forum: x86 64-bit Users
---

### Post by Thelatinprodigy on 2009-07-15
I simply have no sound. My speakers work, they work on windows, and headphones have the same situation. How could I go about trying to fix this?

My sound card is the integrated hda-intel.

---

### Post by anim on 2009-07-16
Which version of ubuntu are you running?

---

### Post by huntzire on 2009-07-16
I have a simlar sound chipset and works fine, however we do need to know what version your ubuntu is.

Alot of times the mixer isnt installed by default which can cause some people issues.

So run though this

Get ubuntu version

do lsmod in command line by going to apps -> accessories -> terminal

type lsmod,

copy and paste that here to see if the hda-intel mod is even being ran,

also double click on your volume buttion and make sure all volume mixer sliders are up, as sometimes on my first install of jaunty it automatically mutes its self when i log in, I dont know why but it does

---

### Post by Thelatinprodigy on 2009-07-16
Jaunty 9.04


Module                  Size  Used by
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
sbp2                   34700  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557492  6 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
arc4                   10240  2 
snd_seq_oss            41984  0 
ecb                    11392  2 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
rt61pci                32260  0 
crc_itu_t              10496  1 rt61pci
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00pci              16768  1 rt61pci
rt2x00lib              43008  2 rt61pci,rt2x00pci
snd_timer              34064  2 snd_pcm,snd_seq
led_class              13064  1 rt2x00lib
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              251528  2 rt2x00pci,rt2x00lib
snd                    78792  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211               43552  2 rt2x00lib,mac80211
soundcore              16800  1 snd
intel_agp              39408  0 
eeprom_93cx6           10624  1 rt61pci
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
pcspkr                 11136  0 
nvidia               8123768  46 
usbhid                 47040  0 
floppy                 75816  0 
ohci1394               42036  0 
ieee1394              108288  2 sbp2,ohci1394
atl1e                  45844  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

It's there, right?

And I know it's not an issue with volume control or anything like that.

---

### Post by Yellow Pasque on 2009-07-17
Look for instructions on configuring /etc/modprobe.d/alsa-base.conf
You need to figure out what HD codec you have.

If you're system is really new, you may need to build the latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

