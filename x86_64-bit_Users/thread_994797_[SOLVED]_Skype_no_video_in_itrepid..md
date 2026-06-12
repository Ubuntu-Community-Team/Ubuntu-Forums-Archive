---
title: "[SOLVED] Skype no video in itrepid."
date: 2008-11-27
forum: x86 64-bit Users
---

### Post by rajeev1204 on 2008-11-27
hi.

I seem to have problems with video on skype in ibex.Its all green and crashes   skype.

I tried some ld=preload hack from a similar thread but it doesnt seem to work.

V4L2 in new kernel seems to be the problem.


Anyone has any ideas?



regards

rajeev

---

### Post by MedellinManDem on 2008-11-27
> **rajeev1204 said:**
> hi.

I seem to have problems with video on skype in ibex.Its all green and crashes   skype.

I tried some ld=preload hack from a similar thread but it doesnt seem to work.

V4L2 in new kernel seems to be the problem.


Anyone has any ideas?



regards

rajeev

mine works fine...

try disabling compiz's video playback setting. that's the only change ive made to any video settings since installing ibex. i dunno if it'll work, but it's worth a try.

---

### Post by rajeev1204 on 2008-11-27
i dont use compiz.

I think ill try using the medibuntu version of skype.

But thanks for responding.Always appreciated . :)

---

### Post by GoLinux on 2008-11-27
rajeev1204,

I had to experiment quite a bit to get video in Skype to work, both transmitted and received. This is what I did:

- First tried Skype using the installer from their website.
- Video received worked, but got the fuzzy green screen when transmitting video.
- Following the advice on this forum, I downloaded and installed the latest version of libv4l from the launchpad website.
- Forced the library to load launching Skype from Terminal using the command " LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype".
- Doing the above fixed the transmitted video (no more green screen!), but I lost received video..... All I could see were random stripes and my image in the lower left corner of the Skype video window.
- I then decided to go for a more radical approach: removed Skype althogether using Synaptic and re-installed Skype-Commonn and Skype-Static taken from Medibuntu web site.
- Now I could start skype normally (no need to do it from Terminal) and get the transmitted video ok (no more green screen), but still couldn't get the received image.
- Suspecting a video driver problem I tried to download the ATI fglrx driver using Application --> Add/Remove, but that messed up all my video setting, so I removed it and went back to the "standard" driver that came with Intrepid.
- At this point I saw this thread and a thought kicked in: Since I have installed Ubuntu 8.10 I have been using it with the default "Normal" setting in "System -> Preferences -> Appearance -> Visual Effect". I tried to set it to "None" and lo and behold, it worked!! I know have video transmitted AND received working in Skype.

F.Y.I., I'm using an old CIF webcam, a trust WB-1400. Considering I'm running Intrepid off a USB Flash Drive (no HDD installation), I'm quite happy of the results!!!

It took me more than a week to get Skype to work (had audio problems as well), but now all is well.

I hope this helps. I outlined all the steps in  case some of the other remedy I tried may work, if just switching to "normal" the Ubuntu visual effects shouldn't work.

Good Luck.

---

### Post by rajeev1204 on 2008-11-28
hi,

Thanks for that.
v
I too tried the medibuntu packages skype common and skype(not the static one) and it worked.

I have a logitech quickcam and video turned out very dark so i installed xawtv and adjusted cam exposure and heh,i got bright video in skype too.:)

Not sure if xawtv saved settings so if someone here could tell me what and where exactly xawtv saves these things , i could probably have bright video after restart too.


But for now,iam marking this thread as solved.




regards

raj.

---

### Post by GoLinux on 2008-11-30
Raj,

glad to see you resolved your problems too. Interestingly, I purchased a Logitech webcam today (I borrowed the Trust WB-1400T from a friend) and I got the dark picture issue too... It is a Logitech Quickcam Chat. 

I had to look around for a while, but then found a control program called v4l2ucp:

[http://www.debian-multimedia.org/dis...ge/v4l2ucp.php](http://www.debian-multimedia.org/dis...ge/v4l2ucp.php)

It allows you to control White Balance, Exposure and Gain of the QuickCam Chat (or any other webcam, I guess)

Once you adjust the parameters, they "stick" after you close it and Chesse, Ekiga and Skype show a decent image.

It is a Terminal application, but it has a graphical front-end. I created a launch icon on the desktop using "Create Launcher..." (right click on the desktop).

I'll give a try to xawtv as well. I believe v4l2ucp has the same issue with the settings, they are kept only until you are in session.

If I found a way to save the settings, I'll post back.

---

### Post by yogo on 2008-11-30
Someone should make this thread a sticky. I finally go my web cam going after a long struggle. I read here and viola I now finally have outgoing video.

My Skype had always worked for incoming video and sound and outgoing sound but no outgoing video. Now my outgoing video works. It works well on 32bit as well.
v412 i386 package works well for Hardy, not sure about Ibex, I have Ibex on another box I may test it tomorrow.
Thanks

---

### Post by GoLinux on 2008-12-01
Yogo,

I'm using 8.10 Intrepid Ibex, as I outlined in my post the Skype "fixes" I described work with a Trust WB-1400T and with the Logitech Quickcam Chat I just got.

With both the Trust and Logitech cams the colors are a little off, with a reddish tint, even after playing with the White Balance control in v4l2ucp.

I tried the Logitech under WinXP with Skype and the original Logitech drivers, the colors are much better. I guess the Linux driver is not fully optimized.

I wish Logitech would develop native Linux drivers for their products, as other manufactures do.

---

### Post by GoLinux on 2008-12-01
LATEST UPDATE: 

I tried another Logitech Webcam, the Quickcam E3560, and it works PERFECTLY with my setup and Skype. No more dark screen, no more colors off, no more need for tweaking with v4l2ucp. I also have WinXP on the same computer and trying skype under WinXP with Skype and the original Logitech drivers for windows yield the same results. I couldn't perceive any noticeable difference when using the cam with WinXP/Skype vs. Ubuntu 8.10/Skype.

For $29.99 this webcam is a steal and it has 640x480 resolution vs. 352x288 plus a built-in microphone that the Quickcam Chat doesn't have (although it comes with a earbud-style headset). For $11 more there is no match with the Quickcam Chat, especially considering how much better it works with Ubuntu 8.10. Another benefit (which I do not know if it is due to the higher resolution or the driver) is that it has a wider angle. Although Skype resizes to 320x240 anyway, the E3560 frames much more than the Quickcam Chat. 

Something to be noted: the E3560 is UVC compliant, so it uses the uvcvideo driver, not gspca_main like the Quickcam Chat. It seems to me either the uvcvideo driver is better or that being a "standard" it goes along perfectly with the webcam.

I couldn't be happier, now that I have a fully functional Ubuntu 8.10 system working out of a 8Gb Flash drive it is like having another computer in my pocket! Even my EVDO Sprint card worked with no tweaking.

:guitar:

---

### Post by gsuarez on 2008-12-14
I'm using a Logitech Quickcam IM 046d:08d9.

I fixed mine by doing the "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" and changing the setting in "System -> Preferences -> Appearance -> Visual 
Effect" to "None".

---

