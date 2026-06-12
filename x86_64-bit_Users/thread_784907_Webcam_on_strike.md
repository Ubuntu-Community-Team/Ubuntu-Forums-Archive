---
title: "Webcam on strike"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by piratebill on 2008-05-06
I am using a logitech web cam that only seems to work sometimes.  When it works, it works absolutely fine.  When it doesn't, the green LED (that normally is on when the cam is in use) is always on and no applications can see the cam.  After many hours of playing with it, I did more harm than good.  After the web cam started working, tvtime no longer sees my tv card anymore.  My tvcard is at /dev/video0 and the cam is at /dev/video1.  After I reboot the camera acts like it did before, only working sometimes.  But now the tvcard doesn't work at all.  Can anyone help me?  they both worked great together in gutsy.


EDIT:
the tv card works fine...the cable is out at my house.  Web cam still only works sometimes though


SOLVED:
the config file for motion (an app that uses a web cam as a security camera) was set to use /dev/video0 and was overriding tvtime

---

### Post by piratebill on 2008-05-07
Ok, the cable here is fine, and now the webcam is working...but the tvcard is still out.  it is possible that the cam drivers are overriding the tvcard?

---

