---
title: "Mouse, touchpad, Nvidia, webcam, NetworkManager and special key"
date: 2006-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by XioNoX on 2006-07-01
Hello,

First I'm french and I haven't a very good english :) 
I've installed ubuntu dapper 64bits on a asus Z92T ([http://www.fnac.com/Shelf/article.asp?PRID=1850497)](http://www.fnac.com/Shelf/article.asp?PRID=1850497)).
Now my uname look like this : Linux laptop 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 x86_64 GNU/Linux

But I have some problems (issues in english ?)
1°/ My Mircosoft (please don't beat me) mouse (USB, wired & optical) don't turn on (no red light of the led) but my touchpad (almost) works
EDIT : I don't know why, but now it work well.

2°/ The touchpad's left button can select text difficultly and couble clik difficultly too.
And I Use qsynaptics to configure the vertical scrolling but I want absolutly to disable the horrisontal scrolling.
EDIT : Half solution : for horisontal scrolling, juste add  Option		"HorizScrollDelta"	"0"  in the synaptics touchpad of xorg.

3°/ I have install the nvidia-glx, remove the dri and change nv to nvidia in xorg.conf, but when I launch google earth the screen bug (I don't know how to explain :/), the same bug hapend when I try to use gnash :/ but glxgears works fine (more than 7000fps).
EDIT : It is the openGL update ot the RAOF eyecandy repos. who don't work for me.

4°/ My webcam seem to be not supported :/ easycam2 don't do anything. I y don't know what I can doo :/ Windows detect it as an asus USB webcam. and lsusb show : Bus 001 Device 004: ID 174f:a311.
EDIT : Drivers in (slow) developpement here : [http://m560x.x3ng.com](http://m560x.x3ng.com)

5°/ NetworkManager show me whell wireless AP and support WPA key, but it don't see my wired conection :/
I must use network-config to use my wired connexion.

6°/ I have an wireless special key (enable/disable wireless) but it don't work. Wireless is always enable, so battries are more used, and I can't use it in plane. So, how make this key work or how turn wireless off ?

It is about all my ubuntu/hardware problemes for the moment.
If you can help me for one of more of these points...

EDIT : 3 bug left :) 

Thanks
XioNoX

---

### Post by XioNoX on 2006-07-02
nobody ?
1°/ I don't know why, but now my mouse work well.

---

### Post by Kilz on 2006-07-02
[QUOTE=XioNoX]nobody ?
1°/ I don't know why, but now my mouse work well.[/QUOTE]
I wish I could help you, but I dont have a laptop , nvidia, or wireless. So I have never ran across these problems.
For the mouse, with it pluged in try this command to try and detect it again.
```
sudo /etc/init.d/udev restart
```

---

### Post by XioNoX on 2006-07-03
I've go back to the 15-23 kernel, and no mouse again.


xionox@laptop:~$ sudo /etc/init.d/udev restart
Password:
 * Loading additional hardware drivers...                                [ ok ]
xionox@laptop:~$

but still no mouse

---

### Post by XioNoX on 2006-07-03
I've update my first post about all solutions I've found.

3 bugs left !

---

### Post by aki-andre on 2006-11-18
Hi!

I have the same problems with same laptop (Z92T) ...

Processor is: AMD Turion 64 x2 ...
Graphic: nVidia 7600 ...

No mouse (on usb),
no Wifi...
no WebCam
no support for flash...

This forum is my only hope :/ 

Pliz... anyone...

---

### Post by aki-andre on 2006-11-19
Finally I made a support to mplayer, flash and java in firefox... The point was that I need to install firefox from architecture 32bit ...
I fallow this how-to [HERE]("http://www.ubuntuforums.org/showthread.php?t=202537")
(meybe someone will need this in the future)

My mouse start working... I don't know why :/ It is really strange... I think this is connected with "noapic" and "nolapic" in the boot krenel options, but now I am not sure why...

Still I don't how WebCam ... And my Broadcom 4318 (WiFi) still don't work...

But now I have less problems than yesterday... and still need a help!

---

### Post by Slade Winstone on 2007-02-12
For a possible fix to your usb mouse problems try:
[http://ubuntuforums.org/showthread.php?t=359482](http://ubuntuforums.org/showthread.php?t=359482)

---

