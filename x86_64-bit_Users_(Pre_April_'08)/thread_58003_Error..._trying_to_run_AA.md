---
title: "Error... trying to run AA"
date: 2005-08-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by fistfullofroses on 2005-08-18
ok so I downloaded and installed America's Army.
all of that went fine (considering that the installer was a script,
and it is hard to have an installer script f--k up).

I have tried to install my video drivers several times and nothing works.
I can use install scripts and everything... and nothing will work.
I have an ATI Radeon X300SE on PCIe (128meg) {issued by Kaser}
But, despite not having drivers loaded I figured I give it a go anyway...

So I went to my terminal and typed armyops...
The load screen came up and then promptly disappeared and what do you know...
and error was listed in the terminal...

[FONT=System]bradford@k8triton:~$ armyops
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
open /dev/[sound/]dsp: Device or resource busy
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error
[/FONT]

last I knew most Linux distros use Xorg by default and not XFree86
and GLX? no idea what that really is...
and sound issues? this is the first sound related problem I have ever really had.
any help? thoughts?
I do not even know if this has anything to do with my graph card, but I think the GLX issue might be something related to it, and it seems there is a config error for sound and general visuals cuz of the device or resource busy thing and the xfree86 thing... beyond that I know nothing. please help.

---

### Post by DancingSun on 2005-08-18
GLX is "OpenGL Extension to the X Window System".  So, looks like the default drivers doesn't work in 3D, or AA doesn't work with software rendering...

As for the sound issue, have you configured sound in GNOME as documented in [www.ubuntuguide.org?](www.ubuntuguide.org?)

---

