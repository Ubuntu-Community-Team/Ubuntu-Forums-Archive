---
title: "Problems with fglrx &amp; ATI Graphics Drivers for Radeon X800, AMD 64, 2 screens"
date: 2005-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by RyanTMulligan on 2005-11-07
Hello Folks,

Here's the deal. I can get two different configurations to "work."

Configuration 1:
Drivers: ATI Proprietary Drivers
Installation Process:
use the .run file to extract the fglrx stuff, then run the fglrxconfig. This then causes problems with the xorg.conf file, involving bad font paths, so I replace the font paths with the old default ones and it works.
Good things:
The taskbar stays only under the left monitor. When windows pop up the pop up centered on the main monitor. 
Problems: 
3D graphics acceleration does not work
Error Associated with this:

```
rmulliga@rtmbox:~$ supertux
supertux: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

This happens with anything using openGL.

Configuration 2:
Drivers: Ubuntu's fglrx packaged drivers
Installation Process: 
Follow this tutorial,[ATI graphics driver tutorial]("http://ubuntuforums.org/showthread.php?p=423589") and do the libria.a replacement.
Then the xorg.conf file still isn't readable, so I copy the old one back in, and it works.
Good things:
Graphics acceleration works, I can run supertux and glxgears and whatever.
Problems:
The task bar goes across both monitors, and doesn't even come up at first, it hides in the left corner, and I have to change the size of it to get it to pop up in the center. If I click the hide button while it is stuck in the bottom left corner it disappears for good. The taskbar across both monitors also means that dialogs and windows popup right between the two monitors so it is impossible to see what is going on with them.

So what I want to do is combine the good things of both of these, and get rid of the problems.

Anyone have any suggestions, or has run in the same problems?

---

### Post by Teroedni on 2005-11-07
for the first one .Do you run sudo?

sudo su

also have you checked if you have libGL.so.1 installed
Go into synaptic aand do a search for it

---

### Post by RyanTMulligan on 2005-11-07
I don't understand your question about sudo.

I installed all this stuff as root of course.

libGL.so.1 is installed. I checked in synaptic like you said to.

---

### Post by Septor on 2005-11-08
The libdrm.a workaround is required for the latest drivers as well.  Also the ati installer will not work correctly on a 64bit system, since on Ubuntu /usr/X11R6/lib points to /usr/X11R6/lib64, not lib32 as it expects.  If you want to run the latest driver check out the Howto (at the new unofficial ATI wiki)

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by RyanTMulligan on 2005-11-09
Thank you for the help. It worked almost like a charm. But it's working now.

---

### Post by stewdog on 2005-11-09
Thanx Septor for the wiki link. 
I followed it precisely but got Mesa output on the fglrxinfo (last step).
When I actually went to /etc/x11/ I noticed that I had a 'xorg.conf.200511092356' file.

After looking at it (and the date/time in the filename), I realised that the parameters within were correct so I commented out the int10 thing and rm'd the xorg.conf.

sudo mv /etc/X11/xorg.conf.200511092356 xorg.conf

Booya. That did it!
Not sure what it was though, 5th day on Ubuntu :)

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.8)

glxgears = 2313.963 FPS

---

### Post by RyanTMulligan on 2005-11-09
Yea I had trouble with the int10 thing as well... I just backed up the package and rm'd it. How did you say you fixed it? I didn't follow your post entirely.

---

### Post by stewdog on 2005-11-10
Sorry about that,
I didn't really have trouble with the int10 entry. The problem I had was that I completed the wiki tutorial for installing the 'newer' ATI drivers, but it did not work until I found the correct xorg.conf.

*** This is not a tutorial but an account of what I did ***

- Ran through the tutorial (I did not see any errors other than the expected dpkg errors and followed the link to resolved them.) 

- Ran glrxinfo (OpenGL version was still Mesa) . Grrr.

- Checked my /etc/x11/ directory for xorg.conf and found a new file called xorg.conf.200511092356. (With numbers corresponding to the current date and time)

- Sudo gedit and removed the int10 line. Also checked that it identified it as ATI and that it specified the correct screen sizes. 

- Backed up the original xorg.conf, then delete it, renamed xorg.conf.200511092356 to just xorg.conf and rebooted.

I have to stress that I don't think all of this was necessary but that's what got it working for me.

I'm also not sure if the int10 line was mentioned in the article but had read it elsewhere and that it should be disabled. 
Hope this makes more sense.

---

