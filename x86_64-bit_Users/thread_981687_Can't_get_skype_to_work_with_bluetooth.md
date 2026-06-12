---
title: "Can't get skype to work with bluetooth"
date: 2008-11-14
forum: x86 64-bit Users
---

### Post by bennig on 2008-11-14
I can't get skype to work with bluetooth on AMD64

I bought a Motorola H375 headset to use with skype, and was able to pair it with my computer. I'm using the latest version of skype. 

When I type this into the terminal:
```
$ arecord -D bluetooth -f s16_LE test.wav
```
I hear a beep in the headset and a message appears at the top right telling me the bluetooth headset has connected. After recording for a few seconds and hitting [ctrl]+[c] terminal returns:
```
Aborted by signal Interrupt...
```
If I try to play the file with:
```
aplay -D bluetooth -f S16_LE test.wav
```
...I end up with:
```
test.wav: No such file or directory
```
If I let it record, without stopping it, eventually it returns:
```
Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 8000 Hz, Mono
ALSA lib pcm_bluetooth.c:460:(bluetooth_hsp_hw_params) BT_SETCONFIGURATION failed : Input/output error(5)
arecord: set_params:962: Unable to install hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 16
CHANNELS: 1
RATE: 8000
PERIOD_TIME: 125000
PERIOD_SIZE: 1000
PERIOD_BYTES: 2000
PERIODS: 4
BUFFER_TIME: 500000
BUFFER_SIZE: 4000
BUFFER_BYTES: 8000
TICK_TIME: [0 0]
```

So far, I have installed blueman and that was helpful in bonding(pairing) the device. I have edited ".asoundrc" a number of times, and right now it looks like this:
```
pcm.bluetooth {
  type bluetooth
  device 00:1F:82:05:0D:16
   profile "auto"
 }
```
   
I have installed, and uninstalled and then reinstalled a number of bluez applications, after following a number of online tutorials. Here's what is installed, according to synaptic when I search for "bluez":
[LIST]
[*]blueman
[*]bluetooth
[*]bluez-audio
[*]bluez-btsco
[*]bluez-cups
[*]bluez-gnome
[*]bluez-hcidump
[*]bluez-pcmcia-support
[*]bluez-utils
[*]btscanner
[*]libbluetooth2
[*]libbluetooth-dev
[*]python-bluez
[/LIST]

When I started this ordeal, in the skype options under "sound devices", a test sound would work if selected as "default device" through my computer speakers, but now that doesn't even work. The test call never worked. I have consistantly gotten the same error: "Problem with Audio Playback". I am totally lost. Sorry, this is a lot, but I just wanted to make sure I gave as much info as possible. Any help would be appreciated.

---

### Post by bennig on 2008-11-14
bump

---

### Post by bennig on 2008-11-19
bump

---

### Post by f.forzano on 2008-12-11
I have the same identical problem, with different hardware.
Using Hardy on a nx7400 hp notebook, and my headeset is a "no brand" giving me the name "BT Headset" after a scan (00:12:C8:04:64:63 is the code).

I hear the initial beep and, after a while, i got the same error message

Another headset (H200...a chinese one) i was unable to authenticate..

There is a way to solve this problem???
tnx

---

