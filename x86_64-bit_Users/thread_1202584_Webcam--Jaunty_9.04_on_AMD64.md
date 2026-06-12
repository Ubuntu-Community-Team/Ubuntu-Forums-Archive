---
title: "Webcam--Jaunty 9.04 on AMD64"
date: 2009-07-02
forum: x86 64-bit Users
---

### Post by suda on 2009-07-02
Hello,

I bought a Logiteck Quickcam Communicate MP S 5500 that was listed as a working camera for Ubuntu.

videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
Bus 001 Device 004: ID 046d:09a1 Logitech, Inc.

Because I cannot "see" this camera when trying it out with Ekiga or "hear" it--I do get a delayed picture with Kopete but no audio--is my issue my AMD64-bit computer? This webcam works when I run it with Vista on 32-bit. 

I want to video conference/chat. How do I get this camera to work with Jaunty on AMD64 bit? Which video conference/chat program do you recommend?

Thanks!

---

### Post by TheBuzzSaw on 2009-07-02
Does this webcam have a microphone built into it? None of mine do. I usually have to plug in a mic separately.

Have you checked the repositories for drivers? I know there are a few in there for Logitech devices.

---

### Post by suda on 2009-07-02
Yep--the mike is built in. I didn't think I had to look for drivers since this is a UVC video device, and I think there's a universal package for this kind of device that comes with Jaunty, drivers and all???

This is what I see in Terminal when I check for the Logiteck webcam:

videodev 45184 2 uvcvideo,compat_ioctl32
v4l1_compat 23940 2 uvcvideo,videodev
Bus 001 Device 004: ID 046d:09a1 Logitech, Inc.

Anybody know for certain if I still need to download drivers---this webcam shows a big green checkmark in the Ubuntu webcam list as a working webcam...


Any ideas on what program is best for video chat/conference that you can get through Synaptic or the Applications link?

---

