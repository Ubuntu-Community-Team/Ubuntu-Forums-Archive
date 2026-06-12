---
title: "Headphone's woln't work"
date: 2009-08-25
forum: x86 64-bit Users
---

### Post by ElevenWarrior on 2009-08-25
I'm running jaunty 9.04 64bit on my 6530, and it doesn't pick up any headphones. at all. Any ideas?

SOLUTION!!!!
SLOVED!!!!!!!!!!!!!! I FINALLY FIGURED IT OUT!!!

here is what I did
open volume control.
under device of HDA ATI SB (alsa mixer)
click preferences
under there click Surround.
worked for me!
only problems I'm having is on my microphone, if I turn it down to a certain level, it switches back to reg speakers.

---

### Post by wfp on 2009-08-26
Have you checked the obvious. Right click on your volume control on your panel> Choose open volume control and under the switches tab make sure you have headphones checked. Make sure your master pcm, and front are not muted.

---

### Post by ElevenWarrior on 2009-08-29
yep already did that. Doesn't even pick up the head phones

---

### Post by zipperback on 2009-08-29
Right click on the speaker icon in your system tray area.

Select "Open Volume Control" from the menu.

Make sure that you don't have something muted.

- zipperback
:popcorn:

---

### Post by Anxious Nut on 2009-08-29
are you using USB headphones?
If yes then read this tutorial carefully [http://www.ubuntugeek.com/ear-candy-a-nice-pulseaudio-volume-manager.html]("http://www.ubuntugeek.com/ear-candy-a-nice-pulseaudio-volume-manager.html")

---

### Post by rhythmiccycle on 2009-08-29
does your sound work at all, or is it only the headphones?

i've had some sound (or no sound) problems the were solved by reloading pulseaudio.

```

sudo killall pulseaudio
pulseaudio

```

---

### Post by Yellow Pasque on 2009-08-29
You probably need to add a model= keyword to /etc/modprobe.d/alsa-base.conf
See: [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by ElevenWarrior on 2009-08-29
okay, nothings muted. 
2. Its regular head phones, audio, and mic not USB
3.killing pulseaduio didn't work.
4. I have a built in headphone on the laptop, could that be part of the problem?

---

### Post by ElevenWarrior on 2009-09-04
agh!  I still can't get it to work!

---

### Post by radioactivet on 2009-09-22
same problem.. help!

---

### Post by ElevenWarrior on 2009-10-02
still nothing... this is sad.. Why woln't the headphones work?

---

### Post by bookgrampy on 2009-10-02
I cannot say what was wrong for me but I just reset (reloaded) BIOS defaults and my sound started working again. To be honest, it was a last resort for me before replacing the MB.

---

### Post by erilidon on 2009-10-03
> **bookgrampy said:**
> I cannot say what was wrong for me but I just reset (reloaded) BIOS defaults and my sound started working again. To be honest, it was a last resort for me before replacing the MB.

yeah I had this problem and it was because my modem was disabled in bios.

---

### Post by ElevenWarrior on 2009-10-06
on the Acer aspire 6530?

---

### Post by ElevenWarrior on 2009-10-06
SLOVED!!!!!!!!!!!!!! I FINALLY FIGURED IT OUT!!!

here is what I did
open volume control.
under device of HDA ATI SB (alsa mixer)
click preferences
under there click Surround. 
worked for me!
only problems I'm having is on my microphone, if I turn it down to a certain level, it switches back to reg speakers.

---

