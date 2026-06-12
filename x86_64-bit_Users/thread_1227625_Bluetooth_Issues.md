---
title: "Bluetooth Issues"
date: 2009-07-30
forum: x86 64-bit Users
---

### Post by aglc2005 on 2009-07-30
I have been trying for about two weeks now to get my stereo bluetooth headset to work properly with Jaunty. The first method I attempted was using the tutorial from Ubuntu, which failed when trying to load the modules. So on I searched and came across Blueman Manager. I have to say that this is a very nice piece of software. I can connect the headset as an Input Device and a Headset, but not as an A2DP device, which from my understanding is what I need to play music through it. Well I reinstalled Bluez in an attempt to see if this would work. It did, I can now connect my headset as an A2DP device through Blueman, but now whenever I try to play any sound on my computer while it is connected, it makes some weird noises, then disconnects and I cannot get it to connect again without rebooting or waiting 15 minutes so. What is going on with it, am I doing something wrong? Below is the output I get when trying to play a sound.

```

$ aplay -D btheadset -f s16_le /usr/share/sounds/ubuntu/stereo/dialog-question.wav
Playing WAVE '/usr/share/sounds/ubuntu/stereo/dialog-question.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Mono
ALSA lib pcm_bluetooth.c:1607:(audioservice_expect) BT_SET_CONFIGURATION failed : Input/output error(5)
aplay: set_params:1022: Unable to install hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 16
CHANNELS: 1
RATE: 44100
PERIOD_TIME: (92879 92880)
PERIOD_SIZE: 4096
PERIOD_BYTES: 8192
PERIODS: 3
BUFFER_TIME: (278639 278640)
BUFFER_SIZE: 12288
BUFFER_BYTES: 24576
TICK_TIME: [0 0]

```

---

### Post by aglc2005 on 2009-08-01
Anyone? I know that bluetooth is not all that common yet, but it would be really nice to get this working.

---

