---
title: "USB Headphones [No Audio]"
date: 2009-09-20
forum: x86 64-bit Users
---

### Post by pmisley on 2009-09-20
Hey.  I have been trying to get my USB headphones to play nicely with Ubuntu and can't seem to make it happen.  I have been googling non-stop looking for answers, but none help me.  I upgraded to the Alsa 1.0.20 driver as I found on one thread.  I simply cannot get any sound to play although it does recognize them.  When I run "aplay -l" I get:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0x47f0xad01 [USB Device 0x47f:0xad01], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am positive from this that the system is at least seeing the headphones.  What is my next step to remedy this problem?  Thanks for any feedback.

Phillip

---

### Post by sookun on 2009-09-21
open terminal

alsamixer

or aumix

then just use arrows to to increase the volumes..guess it should work or system>ad>sound ???

---

### Post by pmisley on 2009-09-21
Alsamixer shows a "Headphone" option that is active and unmuted, however I cannot raise the volume of it.  The volume controls work fine for all the others (Master, PCM, etc.).

---

### Post by Claus7 on 2009-09-21
Hello,

since you have connected your headphones as a usb device, then you have to choose from the sound settings your headphones as a main device. Other than that I do not know how you will be able to have simultaneously sound both from your speakers and your headphones. Of course, doing that, you won't be able to hear sound from your speakers and if you wish so, you have to put back your sound settings to your original ones.

The fact that they are recognized by ubuntu as a usb device, that doesn't mean that you will hear sound from them the moment you plug them.  

Regards!

---

### Post by pmisley on 2009-09-21
Ok.  I have found the options in Applications -> Preferences ->Sound that allow me to switch to my USB device as you mentioned.  Is there any means that will allow the system to auto-switch between headphones or speakers depending on if I have the headphones connected?  If it helps, the headphones are indeed USB and I currently connect them to the front ports of my desktop.  The USB connector on them is a built-in Dolby adapter that can be removed leaving me with a separate headphone/mic jack.  Is it possible to let the OS automatically switch back and forth based on the conditions of receiving or not receiving the signal of the headphones?

---

### Post by Claus7 on 2009-09-22
Hello,

> **pmisley said:**
> Ok.  I have found the ...
glad you did!

> **pmisley said:**
> Is there any means that will allow the system to auto-switch between headphones or speakers depending on if I have the headphones connected? 

My answer to this question is simple as that: if you find out, I would be glad to let me know!

If there is a possibility, I imagine that you have to try some scripting. Apart from that, you could always connect (if possible) your non usb headphones (mine have the ability to be both usb and non-usb ones) to your sound card. That way I do not have to do anything (every time I plug them I have sound), yet only from the one channel of the headset.

edit: sometimes there are some programs like skype, which allow you to have a different sound device as their default one. Yet, if you remove that device (headset) then you have to go manually and change the settings in that program.
Here:
[http://ubuntuforums.org/showthread.php?t=1167678](http://ubuntuforums.org/showthread.php?t=1167678)
I give briefly all the options and combinations that I managed to find available.

Regards!

---

