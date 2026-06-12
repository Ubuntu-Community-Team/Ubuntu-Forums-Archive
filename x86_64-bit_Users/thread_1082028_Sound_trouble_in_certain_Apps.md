---
title: "Sound trouble in certain Apps"
date: 2009-02-27
forum: x86 64-bit Users
---

### Post by kilgore9 on 2009-02-27
Tried posting this in Multimedia but it was ignored and quickly buried... maybe its a 64bit problem anyway.  Using Ubuntu 8.1 64bit on an Acer Extensa 5630.  Sound is generally ok, I get start-up sounds, my music and video players give sound, internet media also puts out sound. 

I get no sound in Skype, Xchat, or the Ekiga Softphone.  In OpenArena, an online FPS, I get sound but it is delayed about half a second.  Very strange!  I would appreciate any help getting my sound to work in all programs.....

---

### Post by Yellow Pasque on 2009-02-27
I believe you have distinct issues that you'll have to fix individually. I would recommend searching for a good guide on pulseaudio setup.

EDIT: On second thought, you should note that the apps you've listed all attempt to access audio at a level lower than pulseaudio (Skype uses ALSA libs directly, Ekiga use libpt/pwlib, (which has an ALSA backend), and Xchat uses aplay. The ALSA/Pulse plugin included in libasound2-plugins should take care of this case, but I have a funny feeling you're experiencing permissions issues with the audio. Try starting the apps from a terminal and see if they give error messages related to the audio.

---

### Post by agarzon on 2009-03-06
Temujin, 

I am having the same problem asdecribed on the beginning of the thread. After starting skype from the command line I get:

agarzon@euler:~/downloads$ skype 
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)

And I don't think I have a bluetooth device

On my other Ubuntu64 machine I fixed the same issue by switching devices in the Sound devices Tab from Default to hw:ati,0, though that didn't work on this machine.

Any other ideas?

---

### Post by Yellow Pasque on 2009-03-06
[https://bugs.launchpad.net/medibuntu/+bug/285412](https://bugs.launchpad.net/medibuntu/+bug/285412)

---

