---
title: "AMD64 + Logitech Quickcam Messenger = HEADACHE!!!!"
date: 2006-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by amcquown on 2006-07-17
I've tried it all, from the qc linux project drivers to looking for workaround install scripts - I cannot get my Logitech Webcam to work under 6.06 64-bit! ](*,) 

Does anyone have any suggestions that may help me? I'm trying to get Camfrog to work under Linux (Wine) but I need the cam working so I can check to see how it handles video.

---

### Post by JoWilly on 2006-07-17
I have the same webcam (Logitech Quickcam Messenger).

It works out of the box here : Pluy and Play :). I just plug it in (USB) and run ekiga for video conferences... works great; nothing to do to get it installed.

---

### Post by amcquown on 2006-07-17
> **JoWilly said:**
> I have the same webcam (Logitech Quickcam Messenger).

It works out of the box here : Pluy and Play :). I just plug it in (USB) and run ekiga for video conferences... works great; nothing to do to get it installed.

Very odd, because it flat-out REFUSES to work. Sure, it shows up when I check what's hooked to my USB ports, and it recognizes the camera properly, but it still will not run, ekiga says the device cannot be found.

---

### Post by JoWilly on 2006-07-17
> **amcquown said:**
> Very odd, because it flat-out REFUSES to work. Sure, it shows up when I check what's hooked to my USB ports, and it recognizes the camera properly, but it still will not run, ekiga says the device cannot be found.

I just tried it again on a fresh amd64 install... still working out of the box.

---

### Post by amcquown on 2006-07-17
I just did a fresh install... Lookie here at this screencap.

[http://i50.photobucket.com/albums/f349/khyberkitsune/ekiga.png](http://i50.photobucket.com/albums/f349/khyberkitsune/ekiga.png)

Note that lsusb properly sees my webcamera, ekiga does not. Nor does Camorama. Ideas?

EDIT: Ekiga *DID* see the Microphone built-into the camera, however.

EDIT-EDIT: I went here [http://www.ubuntuforums.org/showthread.php?t=126053](http://www.ubuntuforums.org/showthread.php?t=126053) and that didn't help even though I've got the exact same model as referenced in that help thread.

---

### Post by JoWilly on 2006-07-17
Hmm.... mine is not reported as a quickcam messenger, but a quickcam web:

```
~$ lsusb

Bus 003 Device 002: ID 046d:0850 Logitech, Inc. QuickCam Web


```

---

### Post by WenSes on 2008-01-11
Hey! eveyone, please somebody help in this forum!! I have the same problem, my cam it's QuickCam Messenger and I'm running the Gutsy Gibbon! still it refuses to anything... I'm getting desperate! 

I tried with quickcam.sh that it's available from [http://home.mag.cx/messenger/](http://home.mag.cx/messenger/) but gives me a lot of trouble because it cannot activate neither the video modules (which at least I can activate in other terminal window) neither the webcam driver.

Could somebody give us a clue???


Thxs

---

### Post by magikx21 on 2008-01-11
Have you tried Camstream. I had some issues getting my webcam to work but after I tried Camstream it worked fine and then began working in all other programs. Not to sure why or how this worked for me but maybe it will for you too.

---

