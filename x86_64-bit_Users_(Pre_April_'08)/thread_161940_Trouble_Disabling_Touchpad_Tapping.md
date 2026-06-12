---
title: "Trouble Disabling Touchpad Tapping"
date: 2006-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anthron on 2006-04-18
First off, let me say that Ubuntu is a beautifully put together distro. I feel like it came with the right amount of applications, not too many, not too few. It was exetremely easy to install (I finally have something to recommend to friends), its hardware support is receiving an A+ right now as far as I'm concerned (my powerbook's touchpad works out of the box!), and its default look is actually a healthy balance of unobtrusive and attractive.

Now that I have gotten that out of the way, I can't seem to disable touchpad tapping on my powerbook. I've never had it enabled, and I never use it. I find it a bit annoying. I went into /etc/X11/xorg.conf and added the line

> Option "TapButton1" "0"

and rebooted, but I got no result. I then added

> Option "MaxTapTime" "0"

and rebooted, but still no result. Out of frustration, I commented out the entire section for my touchpad, and the InputDevice "Synaptics Touchpad" line, and rebooted. To my amazement my touchpad was still working. Obviously I'm modifying the wrong file.

I thought that perhaps there would be another x configuration file in my home directory, but a "ls -a" proved that wrong.

What should I do?

[Edit]I forgot to mention, this is on a 15" Powerbook, 1.67ghz G4[/Edit]

---

### Post by Anthron on 2006-04-19
I'd hate to bump, but I'm still looking for the answer to this problem :???:

---

### Post by nickleus on 2006-04-21
I am also having trouble disabling touchpad tapping. I'm using a Dell Inspiron 510m laptop.
I have tried using tpconfig and that didn't work. I've tried setting values from the command line:
```
synclient MaxDoubleTapTime=0
synclient MaxTapTime=0

```
and that didn't help either. I've even edited the */etc/X11/xorg.conf* file like everyone else says:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "MaxTapMove"            "0"
        Option          "MaxTapTime"            "0"
        Option          "tapbutton1"            "0"
        Option          "SHMConfig"             "on"
EndSection
```

but that hasn't helped. It is driving me crazy! The xorg.conf trick works on Fedora Core 4, but not with Ubuntu 5.10. What is the solution? Anybody? Thanks in advance =)

---

### Post by Lucky. on 2006-05-05
Hey Guys,

Well gee, I was looking around trying to find out how to disable my touchpad tapping, and found this post.  I did exactly what Anthron said (added in both lines), and it worked!  Rebooted and everything was fine...

Sorry, I know this can't be much of a help, but it does appear that you are doing the right things at least...

---

### Post by dmjones500 on 2007-10-19
Yup, worked for me too on a Dell Latitude D420.

FYI, you don't need to reboot after changes to xorg.conf.  If you just do a "Ctrl-Alt-Backspace", it will restart the xserver, which is sufficient to re-read changes to xorg.conf (and much much quicker).

It does, however, log you out, so make sure you safe stuff etc...

---

