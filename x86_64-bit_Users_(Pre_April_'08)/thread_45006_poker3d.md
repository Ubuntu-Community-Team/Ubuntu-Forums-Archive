---
title: "poker3d"
date: 2005-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by skylark on 2005-06-28
Recently I've been playing a bit of poker at [www.pokerroom.com](www.pokerroom.com) since it has a java client interface. After losing some real money there though I thought I should try and wean my self off it and find another poker game I could play online (if I visit that site I might be tempted to play real money again :-( ! )

So I tried poker3d. When I run it I see the splash screen then a few seconds later the program crashes. Here is the error:

loading file:/home/user0/.poker3d/poker.client.xml
loading file:/etc/poker3d/client/client.xml
loading file:/usr/share/underware/poker/data/player.male.cal3d/cal3d.xml
open /dev/[sound/]dsp: Device or resource busy
No OpenAL EAX2.0 extensions available
Xwnc kill(7818,9) : [Errno 3] No such process
Xwnc: /usr/bin/Xwnc -localhost -auth /unlikely-to-exists -to 200000 -rfbwait 180000 -depth 24 -geometry 1280x1024 :1
.2005-06-28 22:53:48 Xwnc version 1.0.0
2005-06-28 22:53:48 Copyright (C) 1999 AT&T Laboratories Cambridge.
2005-06-28 22:53:48 Copyright (C) 2000-2002 Constantin Kaplinsky.
2005-06-28 22:53:48 Copyright (C) 2003 Olivier Chapuis.
2005-06-28 22:53:48 Copyright (C) ...etc see the source code
2005-06-28 22:53:48 All Rights Reserved.
2005-06-28 22:53:48 Desktop name 'x11' (machine0:1)
2005-06-28 22:53:48 Protocol version supported 1.0
2005-06-28 22:53:48 Listening for WNC connections on TCP port 5901
2005-06-28 22:53:48 Use default RGB format
2005-06-28 22:53:48 RGB format 8 8 8

2005-06-28 22:53:49 Got connection from client 127.0.0.1
2005-06-28 22:53:49 rfbProcessClientProtocolVersion: client gone
2005-06-28 22:53:49 Client 127.0.0.1 gone
2005-06-28 22:53:49 Statistics:
2005-06-28 22:53:49   framebuffer updates 0, rectangles 0, bytes 0
 poker3d-interface kill(7819,9) : [Errno 3] No such process
poker3d-interface: /usr/bin/poker3d-interface -r /usr/share/underware/poker/data/interface/gtkrc --verbose 0 --display :1 --port 19379
cat: /unlikely-to-exists: No such file or directory
The program 'poker3d-interface' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 7 error_code 2 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

2005-06-28 22:53:52 Got connection from client 127.0.0.1
2005-06-28 22:53:52 Protocol version 1.0
2005-06-28 22:53:52 Pixel format for client 127.0.0.1:
2005-06-28 22:53:52   32 bpp, depth 8, little endian
2005-06-28 22:53:52   true colour: max r 255 g 255 b 255, shift r 0 g 8 b 16
2005-06-28 22:53:52 Xwnc Pixel format:
2005-06-28 22:53:52   32 bpp, depth 24, little endian
2005-06-28 22:53:52   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
2005-06-28 22:53:52 Using raw encoding for client 127.0.0.1
2005-06-28 22:53:52 Enabling cursor position updates for client 127.0.0.1
2005-06-28 22:53:52 Enabling X-style cursor updates for client 127.0.0.1
2005-06-28 22:53:52 Enabling window shape for client 127.0.0.1
Warning: non texture attribute 'BlendFunc' passed to setTextureAttributeAndModes(unit,attr,value),
         assuming setAttributeAndModes(attr,value) instead.
         please change calling code to use appropriate call.
Warning: non texture attribute 'Material' passed to setTextureAttributeAndModes(unit,attr,value),
         assuming setAttributeAndModes(attr,value) instead.
         please change calling code to use appropriate call.
Warning: non texture attribute 'Material' passed to setTextureAttributeAndModes(unit,attr,value),
         assuming setAttributeAndModes(attr,value) instead.
         please change calling code to use appropriate call.
Warning: non texture attribute 'Material' passed to setTextureAttributeAndModes(unit,attr,value),
         assuming setAttributeAndModes(attr,value) instead.
         please change calling code to use appropriate call.
Warning: non texture attribute 'Material' passed to setTextureAttributeAndModes(unit,attr,value),
         assuming setAttributeAndModes(attr,value) instead.
         please change calling code to use appropriate call.
Warning: non texture attribute 'Material' passed to setTextureAttributeAndModes(unit,attr,value),
         assuming setAttributeAndModes(attr,value) instead.
         please change calling code to use appropriate call.
Warning: non texture attribute 'Material' passed to setTextureAttributeAndModes(unit,attr,value),
         assuming setAttributeAndModes(attr,value) instead.
         please change calling code to use appropriate call.
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
SoundManager::~SoundManager()SoundManager::shutdown() should be called for the SoundManager before the deconstructor is called
2005-06-28 22:53:55 Client 127.0.0.1 gone
2005-06-28 22:53:55 Statistics:
2005-06-28 22:53:55   framebuffer updates 0, rectangles 0, bytes 0

Any ideas? Anyone got poker3d working on an AMD64 machine? 

PS: The error complains "/dev/[sound/]dsp: Device or resource busy" which is weird since it should be free (I did a clean reboot and didn't open any apps). esd was using /dev/dsp but even after killing this poker3d would still not run (plus it then stuffed up my sound for every other application I tried to run).

---

### Post by skoal on 2005-06-28
lmao.  You too? I already tapped out my credit cards and put a second mortgage on my house, all because of pokerroom.com.  I keep a browser window open on that site 24x7.  I tried out poker3d as well.  It loads up fine, takes me to the barn with the table and chairs, then I try to move around the room a bit, and then it crashes and leaves my mouse cursor all limp on the desktop.

My error seems different than yours (but occurs at the same time).  I'm on a P4 kernel /Nvidia box btw.  Maybe we'll figure this out together and see if we can't keep the shirts on our backs this way.

\\//_

---

