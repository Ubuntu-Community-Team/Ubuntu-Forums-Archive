---
title: "New User - more AMD 64 Wine Installation Errors"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by brent09 on 2006-09-22
Hi,
I'm totally new to ubuntu so I'm not all that familiar with how things work.

I've been trying to install Wine to my AM2 AMD Athlon 64 3200+.  I did some searching around after realizing it couldn't be done quickly through Synaptic  and found the following thread by kilz: [http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)

I went through the steps listed there and everything seemed to go well until I test it by entering winecfg into the terminal.  Then I get the following errors:

```
brent@brent-amd64:~$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

```

If anyone can suggest possible solutions for me it'd be appreciated.  If more information is required I'll do my best to provide it, but keep in mind that this OS (and linux in general) is new to me.
Also, if it is necessary to remove Wine before giving all of this another attempt I'll probably need some instruction on how to get rid of what I've done so far.

I appologize if this error has been adressed previously.  I was unable to find it.
Thanks in advance,

---

### Post by Kilz on 2006-09-22
> **brent09 said:**
> Hi,
I'm totally new to ubuntu so I'm not all that familiar with how things work.

I've been trying to install Wine to my AM2 AMD Athlon 64 3200+.  I did some searching around after realizing it couldn't be done quickly through Synaptic  and found the following thread by kilz: [http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)

I went through the steps listed there and everything seemed to go well until I test it by entering winecfg into the terminal.  Then I get the following errors:

```
brent@brent-amd64:~$ winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15

```

If anyone can suggest possible solutions for me it'd be appreciated.  If more information is required I'll do my best to provide it, but keep in mind that this OS (and linux in general) is new to me.
Also, if it is necessary to remove Wine before giving all of this another attempt I'll probably need some instruction on how to get rid of what I've done so far.

I appologize if this error has been adressed previously.  I was unable to find it.
Thanks in advance,

open a terminal, type in ```
glxinfo
``` and copy the results back here.

---

### Post by brent09 on 2006-09-22
hrm... it gave me an error during that as well...

```
brent@brent-amd64:~$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
brent@brent-amd64:~$

```

---

### Post by Kilz on 2006-09-22
> **brent09 said:**
> hrm... it gave me an error during that as well...

```
brent@brent-amd64:~$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  0 0 None
brent@brent-amd64:~$

```

The reason for that error and the orignal one is you need to install the drivers for video card.[ Go here ]("https://help.ubuntu.com/community/BinaryDriverHowto")and click on the link for your card.

---

### Post by brent09 on 2006-09-22
okay... I'm writing from the liveCD now. :rolleyes: 
I managed to mess-up something on my X configuration (?? I think...) while trying to install the driver for my 7600 GT.  It kept saying that something had been changed and the operation could not proceed, then suggested a command to fix my troubles.  Long story short, I'm reinstalling the OS.

Hopefully with a clean install (not that I had done much on the previous one), things will go more smoothly.

Thanks for the help Kilz.  I'm sure I'll get this figured out eventually.  Just have to climb up the learning curve a little bit farther.

---

### Post by Kilz on 2006-09-22
> **brent09 said:**
> okay... I'm writing from the liveCD now. :rolleyes: 
I managed to mess-up something on my X server (?? I think...) while trying to install the driver for my 7600 GT.  It kept saying that some configuration had been changed and the operation could not proceed, then suggested a command to fix my troubles.  Long story short, I'm reinstalling the OS.

Hopefully with a clean install (not that I had done much on the previous one), things will go more smoothly.

Thanks for the help Kilz.  I'm sure I'll get this figured out eventually.  Just have to climb up the learning curve a little bit farther.

The video card drivers would be the very first thing I would install if I were you. They can be a pain regardless of version, especialy to a new user. 
The first month or 2 is the worst of the learning curve. At least thats what I thought was the worst. keep trying and asking questions, especialy about the video card drivers.

---

### Post by brent09 on 2006-09-22
> **Kilz said:**
> The video card drivers would be the very first thing I would install if I were you. 

That's my approach this time.

I'm following the steps here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Right now I'm working on step 10.
I've had to restart once after installing a new kernel module for k8 architecture.

I'm now getting the following error on my fresh install.
```
brent@brents-amd:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
brent@brents-amd:~$

```

It was by exectuing this command that I got myself into trouble last time so I'm reluctant to do it again.  Suggestions?
I'll be looking around a bit for answers in other threads as well.

---

### Post by Kilz on 2006-09-22
> **brent09 said:**
> That's my approach this time.

I'm following the steps here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Right now I'm working on step 10.
I've had to restart once after installing a new kernel module for k8 architecture.

I'm now getting the following error on my fresh install.
```
brent@brents-amd:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
brent@brents-amd:~$

```

It was by exectuing this command that I got myself into trouble last time so I'm reluctant to do it again.  Suggestions?
I'll be looking around a bit for answers in other threads as well.

I have ATI graphics so I'm not an expert on nvidia. If you are having problems with the driver[ Easyubuntu]("http://easyubuntu.freecontrib.org/get.html") can install the official driver for you.

---

### Post by brent09 on 2006-09-22
I think I may have jsut got it by piecing together a few comments of user tselliot's that I found in a search.  Infact, it was as simple as chaning nv to nvidia in xorg.conf.  But I had no idea how to do so at first since it was coming up as read-only in gedit.  
Anyways, when I figured it out it gave me a NVidia splash screen before my login screen - I assume that's a good sign.

[QUOTE=nvidia driver install steps]If you see an NVIDIA splashscreen after hitting Ctrl-Alt-Backspace, your drivers are properly installed.[/QUOTE]

I get a massive matrix shown to me now when i enter glxinfo, and no error message.

I'll keep hacking away here until I break something.  If nothing else, I'll at least learn a thing or two.


I hope now that I'm ready to try isntalling Wine again. **Fingers crossed**

---

### Post by brent09 on 2006-09-23
Everything seems to be working properly.  I tested Wine out by quickly installing Winamp 5 and it works as expected.

Kilz, I can't thank you enough for the assistance.:wink:
I might have figured it out... *eventually*, but there would have been far more hairpulling involved.

---

### Post by Kilz on 2006-09-23
> **brent09 said:**
> Everything seems to be working properly.  I tested Wine out by quickly installing Winamp 5 and it works as expected.

Kilz, I can't thank you enough for the assistance.:wink:
I might have figured it out... *eventually*, but there would have been far more hairpulling involved.

Your welcome, part of Ubuntu is helping others. It gets addictive :D  If you have any more questions just post back.

---

