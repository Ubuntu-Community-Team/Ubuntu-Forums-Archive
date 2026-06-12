---
title: "PVR150 Trouble"
date: 2005-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by FluffyElmo on 2005-09-07
I've installed a PVR150 (retail) TV-tuner capture card on Hoary amd54 and have been having some issues. When I try to make the ivtv utils I get the following error:
```

ivtvctl.o(.text+0x611): In function `pts_to_string':
: undefined reference to `ceilf'
```

The device manager also shows the compression device, but there is no mention of a tuner...not sure if there should be or not.

On the positive side, the ivtv driver is installed and working, cp /dev/video0 test.mpg and mplayer /dev/video0 both produce video. So I think I'm close...it feels like I just have to fix a few glitches and I'm there.

As always, any help greatly appreciated...

---

### Post by SickTwist on 2005-09-19
[QUOTE=FluffyElmo]I've installed a PVR150 (retail) TV-tuner capture card on Hoary amd54 and have been having some issues. When I try to make the ivtv utils I get the following error:
```

ivtvctl.o(.text+0x611): In function `pts_to_string':
: undefined reference to `ceilf'
```

The device manager also shows the compression device, but there is no mention of a tuner...not sure if there should be or not.

On the positive side, the ivtv driver is installed and working, cp /dev/video0 test.mpg and mplayer /dev/video0 both produce video. So I think I'm close...it feels like I just have to fix a few glitches and I'm there.

As always, any help greatly appreciated...[/QUOTE]
 It sounds like there's a bug in the code. If so, it may have already been fixed. Have any newer versions of the ivtv utilities been released since you last tried compiling them?

If not, you might want to pass your question along to the ivtv developers list to see if they know about it and/or could suggest a fix.

Keep us posted.

---

### Post by FluffyElmo on 2005-09-19
Sorry, I should have kept this thread updated as I now have it working. My original problem seemed to be with the 0.3.8 driver, the utils for the 0.3.7k driver compiled without a hitch. 

So right now I'm running the 0.3.8 driver with the 0.3.7k utilities, which is probably not recommended but everything works just fine. Overall, I'm very happy with this card, for the relatively low price video and audio quality are excellent while the CPU usage is virtually unnoticeable.

I just noticed they have a 0.3.9 driver, I may try compiling that when I go home to see if the problem has been fixed.

---

