---
title: "fglrx vs ATI driver in Breezy AMD64 version"
date: 2006-01-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by nbhaskar on 2006-01-11
When I run the fglrxinfo I get the following

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

It seems like it is using fglrx driver, How to set up the latest ATI driver?

---

### Post by gunksta on 2006-01-13
fglrx IS ATI's binary driver, sad though that might be.  What kind of a graphics card are you using?  The version of fglrx that shipped with Breezy is 8.16.8 I believe, and it has some notable issues with some video cards.  For instance, on my laptop i have to disable the onboard RAM when using the fglrx driver or X locks up.  

This is **NOT** Ubuntu's fault.  It's not even X's fault.  ATI screwed up the driver.  It's their fault.  Looking at the ATI web-page, I notice that they have released several versions since then, or they released once and bumped their numbers way up. Either way, it's a new driver.  

I like managing things through Synaptic and the repos that are as important as my video driver, so I'm going to wait for Dapper and upgrade then.

Did you use Synaptic to get fglrx or did you get the driver directly from ATI?

---

### Post by nbhaskar on 2006-01-15
[QUOTE=gunksta]fglrx IS ATI's binary driver, sad though that might be.  What kind of a graphics card are you using?  The version of fglrx that shipped with Breezy is 8.16.8 I believe, and it has some notable issues with some video cards.  For instance, on my laptop i have to disable the onboard RAM when using the fglrx driver or X locks up.  

This is **NOT** Ubuntu's fault.  It's not even X's fault.  ATI screwed up the driver.  It's their fault.  Looking at the ATI web-page, I notice that they have released several versions since then, or they released once and bumped their numbers way up. Either way, it's a new driver.  

I like managing things through Synaptic and the repos that are as important as my video driver, so I'm going to wait for Dapper and upgrade then.

Did you use Synaptic to get fglrx or did you get the driver directly from ATI?[/QUOTE]


I've ATI X700 256MB card and I got the fglrx driver from synaptic. Thanks for the info.

Cheers.

---

### Post by RAOF on 2006-01-15
Here's a [howto]("http://www.ubuntuforums.org/showthread.php?t=75378") for getting the (latest?) 8.16.20 fglrx drivers working in Breezy.  Hope it helps, I've got an nvidia card.  They seem to just work(tm) ;)

---

### Post by DeDua on 2006-01-16
You need to change a file  libdri.a with that one which is in the post above (link) of course libdri for amd64 :) and it should help.

---

### Post by Septor on 2006-01-18
I have submitted new packaging scripts to ATI which will fix the libdri.a issue for all amd64 Ubuntu users.  It should be incorporated in the next driver release from ATI.  Hopefully this will make it much easier for Breezy-64 users to get up and running with ATI's driver.

---

