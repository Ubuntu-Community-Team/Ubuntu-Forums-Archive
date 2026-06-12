---
title: "Zoneminder freezing"
date: 2009-08-30
forum: x86 64-bit Users
---

### Post by jhetrick62 on 2009-08-30
I'm having the toughest issue to diagnose and I do believe it may be hardware related, but I wanted to see if anybody else experienced this.

I'm running Ubuntu x64 LTS 8.04 and the ZM v 1.22.3 which comes in the stable repos for Ubuntu Hardy.  BTW, I have installed this before, but on a difference Motherboard, otherwise I have used this exact same combination and still have it running on another server.

The current install however, freezes somewhere in between 12 & 24 hours of continuous operation on the capture daemons.  I elevated the debug logs and it reports that it catches a "system interrupt" and stalls.  I can't find the issue in the messages or dmesg logs.  

When I attempt to wget the image file from the camera, I can't connect!  It's as if the linux box is ignoring the http request altogether as it doesn't even reach the camera.  What makes it worse, is it only freezes the first (4) cameras, not the last two (I have six total)!!  I find this totally bizarre.

When it's froze, I use the command wget [http://user:password@192.168.0.10:86/jpg/image.jpg](http://user:password@192.168.0.10:86/jpg/image.jpg) and it won't allow me through to even connect to the camera although it's fine when the daemon hasn't frozen.  Same with ports 88, 89 and 90 which are all cameras #1-#4 in zm.  Now for ports 92 & 93 (cams 5 & 6 in zm) it doesn't freeze in zm and I can still use wget.

So I'm totally baffled as to what is happening.  As I said, I have another duplicate system that runs flawlessly and the only difference in the mobo and processor.  This one is a Biostar w/ a dual core athlon chip an the working one that never freezes is a Biostar with a quad core athlon.

Any thoughts on where to take this.  I plan to install a 32 bit version into my VirtualBox on the same box to see if it acts the same?

Any thoughts on what part of the server OS is actually locking up as it won't allow me to do a manual http download using wget once this happens?

Any thoughts are appreciated.
Jeff

---

