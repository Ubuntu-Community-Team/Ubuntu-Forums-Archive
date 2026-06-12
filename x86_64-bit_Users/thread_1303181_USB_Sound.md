---
title: "USB Sound"
date: 2009-10-27
forum: x86 64-bit Users
---

### Post by weaselnet on 2009-10-27
I have spent several hours reading forums to end up no where. How in the world do you tell ubuntu to use a usb sound device as default? I have experimented with several explanations to end up with the same failed results. Right now I show my on board audio device with an index of 0 and it is listed as snd_hda_intel. My usb device lists as an index of 1 and snd_usb_audio. Does anyone have a solution that can guide me through switching these index priorities?

---

### Post by timgood on 2009-10-28
You do not say what version of Ubuntu you are using, or if you are using PulseAudio. If you are, then right clicking on the speaker icon in the system notification tray will bring up a context menu. Select Sound Preferences which will bring up a window allowing you to choose the default input and output devices. I hope this helps.

---

### Post by weaselnet on 2009-10-28
O.K. So here are some more specifics. I am running UE 2.3 based on jaunty. Pulse audio will allow applications to specify which device to use, but the o/s still defaults to the index 0 device which is the snd_hda_intel. So firefox will defualt to that sound device and I would like it to use the other.

---

### Post by timgood on 2009-10-29
Installation of PulseAudio device chooser and PulseAudio volume control will enable you to run sound streaming (for example) from Firefox and direct the output to your USB sound device. I do this with Skype and it works very well. PulseAudio Volume Control needs to be running at the same time as your streamed sound - you can then change the stream to always run on the specified device.

---

