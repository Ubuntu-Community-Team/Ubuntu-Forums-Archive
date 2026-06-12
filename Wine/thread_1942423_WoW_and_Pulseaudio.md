---
title: "WoW and Pulseaudio"
date: 2012-03-17
forum: Wine
---

### Post by Dekafox on 2012-03-17
I'm using Wine 1.4 right now on Xubuntu 12.04b1.  Here's the issue:

In a nutshell, Wine is going straight to HW and not letting me tell it to use Pulseaudio.

In 10.04 with 1.3 I was able to get it to run ALSA through Pulse.  Now, when I launch WoW, nothing else is able to use the same device.  The sound options within WoW only list hardware devices apart from the System Default(i.e. no option to select PulseAudio).  When I do lsof /dev/snd/* I get


COMMAND     PID     USER   FD   TYPE DEVICE SIZE/OFF  NODE NAME
xfce4-vol  1748 ****    8u   CHR  116,7      0t0  7655 /dev/snd/controlC0
xfce4-vol  1748 ****   11u   CHR 116,16      0t0  7895 /dev/snd/controlC1
xfce4-vol  1748 ****   14u   CHR 116,19      0t0 11339 /dev/snd/controlC2
pulseaudi  1754 ****  mem    CHR 116,17          11337 /dev/snd/pcmC2D0p
pulseaudi  1754 ****   22u   CHR 116,16      0t0  7895 /dev/snd/controlC1
pulseaudi  1754 ****   23u   CHR 116,16      0t0  7895 /dev/snd/controlC1
pulseaudi  1754 ****   29u   CHR 116,17      0t0 11337 /dev/snd/pcmC2D0p
pulseaudi  1754 ****   30u   CHR  116,7      0t0  7655 /dev/snd/controlC0
pulseaudi  1754 ****   35u   CHR  116,7      0t0  7655 /dev/snd/controlC0
pulseaudi  1754 ****   37u   CHR  116,7      0t0  7655 /dev/snd/controlC0
pulseaudi  1754 ****   42u   CHR 116,19      0t0 11339 /dev/snd/controlC2
pulseaudi  1754 ****   48u   CHR 116,19      0t0 11339 /dev/snd/controlC2
WoW.exe   17711 ****  151u   CHR  116,4      0t0  7652 /dev/snd/pcmC0D0p

And Pulseaudio doesn't even see the stream from WoW.  

How can I force ALSA to run through pulse?  Or at least connect to the right device so it'll share audio with other programs?

---

### Post by cwwilson721 on 2012-03-17
I use the following ([COLOR="red"]edited for my own setup[/COLOR]) command to launch WoW with a Pulse Audio "wrapper":
```
env WINEPREFIX="/home/<USER>/.wine-wow" [COLOR="Red"]padsp wine "C:\Program Files\World of Warcraft\Wow.exe"[/COLOR] -opengl
```
Seems to work well for me

---

### Post by Dekafox on 2012-03-18
Hmm... I'd tested that before with WoW and it hadn't worked, but it seems to be working now.  I thought that'd changed with wine 1.4 but I guess I was wrong!

Just so this thread isn't a total waste, I'll add that d3d11 mode works great with Wine 1.4.  I've got shadows(which are disabled in OpenGL mode) among other things, and I'm still getting 40-60 fps in raid, and 40 in Stormwind even.

---

### Post by cwwilson721 on 2012-03-18
For most wine/WoW users, using D3D will kill FPS.

If you have "high horsepower", you'll be fine, but the majority have mid to low end graphics and CPUs.

Just so you know, there is no "native" Linux D3D, so wine dll's for D3D actually "convert" the calls to OpenGL, and then send it to the hardware.

That extra step can kill FPS, so that is why OpenGL mode is preferred.

---

