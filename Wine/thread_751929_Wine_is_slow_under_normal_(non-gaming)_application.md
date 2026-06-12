---
title: "Wine is slow under normal (non-gaming) applications..."
date: 2008-04-11
forum: Wine
---

### Post by krlhc8 on 2008-04-11
I keep reading threads like: "I WOW3 lags a bunch under wine" etc.  But I can't even get standard GUI apps to run sans lag.  I'm an EE major and have quite a bit of projects I'm working on with Eagle and Keil uVision, and they work in theory, but they're too laggy to operate without a headache. 

Keil uVision has a simple text editor for editing C code, and when I try to move the cursor around with my keyboard, it lags for like two seconds per cursor move.  Typing is a pain, too, as it lags an additional second per keystroke.  And the menus lag like five seconds to click and a second to scroll.  

WineHQ says that Keil uVision works perfectly, so I know it's something I'm botching up.  Any help quickly would be much appreciated.

Eagle is much the same lag pain, so I'm again reassured that it's not the software but maybe drivers and/or wine config.

Here are my computer specs: 
[http://support.gateway.com/s/Mobile/Q106/BladeC/1013928Rsp2.shtml](http://support.gateway.com/s/Mobile/Q106/BladeC/1013928Rsp2.shtml)

Let me knock out some questions for you all:
In the terminal I typed: *glxinfo | grep vendor*
and received:
[I]server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc[/I]

Then I typed:* glxinfo | grep 'OpenGL version'*
and received:
*OpenGL version string: 1.3 Mesa 7.0.1*

I'm not sure where to go from here...

---

### Post by krlhc8 on 2008-05-15
Wine 1.0 r-1 came out and solved all my problems.  It's amazing!  Although I switched to Eagle on Linux, and as expected, it works better.  Figuring out Eclipse with SDCC would be ideal to replace Keil uVision.  I have it installed, yet it's very difficult to figure out what the compile settings need to be.  I'm sure there's a thread somewhere out there.

---

