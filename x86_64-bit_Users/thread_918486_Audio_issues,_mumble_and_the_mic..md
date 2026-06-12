---
title: "Audio issues, mumble and the mic."
date: 2008-09-13
forum: x86 64-bit Users
---

### Post by DanDwalker on 2008-09-13
Hi, i apologize i am a complete noob when it comes to linux and recently made a cold turkey swap using vmware to support my needs for windows (zune and other pieces of hardware).

Before making the switch I was using mumble as the voip of choice, however currently i can not get any output.  I have gone through and configured mumble to set up a loop back and have no clue where anything is in ubuntu to even troubleshoot this issue at all.  As well i am using an analog mic straight into my 3.5mm jack.

PC Specs:

Maximus Formula mobo w/ the Supreme FX II sound card it comes with

and if it makes a difference doubt it does but
4GB of memory and an 8800GT

So once again just going to state that i am a complete noob and am trying to move over to linux and just having some difficulties so any explanations or ideas would be helpful and the more detail the better.  Posted in the 64-bit user thread because i am using the x86 user build of 8.04

Thanks a ton (Going to bed now but will be checking thread tomorrow when i get out of work)
-DanDWalker

---

### Post by soxs on 2008-09-13
What audio backend are you using? Alsa or Pulseaudio? In case you are using PA, .. I had serious mic troubles and switched to ALSA and all the noise and blurring were gone.
You may try iot woithout any risk by goingto:
"System -> Preferences -> Audio"
and set verything to ALSA (where it is possible)

EDIT: Btw, you should update to 1.1.5 (get it from [www.getdeb.net](www.getdeb.net))

---

### Post by DanDwalker on 2008-09-13
thanks for the response, went in and attempted to change my sound capture over to ALSA and i am getting a message coming up with 

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat; Could not open audio device for recording. Device is being used by another application.

so not sure, don't have an application that is using the mic however not quite sure what is going on.  going to price out a usb mic today at work and see what i can do there as i think that would be cheaper but wouldn't mind overcoming this issue as well

---

### Post by soxs on 2008-09-13
> **DanDwalker said:**
> thanks for the response, went in and attempted to change my sound capture over to ALSA and i am getting a message coming up with 

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat; Could not open audio device for recording. Device is being used by another application.

so not sure, don't have an application that is using the mic however not quite sure what is going on.  going to price out a usb mic today at work and see what i can do there as i think that would be cheaper but wouldn't mind overcoming this issue as well

Try to reboot and retest. maybe PA is still running and "using" (or capturing) the mic and so blocking alsa from using it.

---

