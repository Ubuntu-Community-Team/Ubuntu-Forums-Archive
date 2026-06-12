---
title: "Playing sound from a 32bit app on a 64bit system with pulse"
date: 2007-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomscl on 2007-06-28
Hi there,

This is my first post here and my first experience with ubuntu, we have made the descision to switch the office over to ubuntu after many years of using fedora, so far so good but now I have a problem...

We are using LTSP so the users are working from diskless clients to log into a 64 bit (intel core 2 duo) server running the 64 bit version of ubuntu, the sound works perfectly. That is until a 32 bit binary tries to play a sound...

The example I've been working with is skype, inorder to use skype I have installed the lib32asound2 package, now I believe that if I was running on a stand alone machine then I think this would probably work fine however what I get is:

ALSA lib ../../../src/control/control.c:875:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

(note this only occures when running 32bit binaries).

The reason I believe this is occuring is because /usr/lib/alsa-lib/libasound_module_ctl_pulse.so, which is provided by libasound2-plugins, is a 64 bit library and therefore can't be loaded by the 32 bit version of alsa. What I was hoping for was to find a lib32asound2-plugins package which would make my problems go away but it appears no such package exists.

I have tried getting the 32bit libasounds2-plugins package and copying the .so files to both /usr/lib/alsa-lib/ and /usr/lib32/alsa-lib/ (clutching at straws) but neither of these attempts seemed to solve the problem.

Does anyone have any suggestions on what I could try next or has anyone else experienced this problem? The next thing I could think of would be to try to recompile the lib32asound2 and attempt to create a matching lib32asound2-plugins package but this seems quite drastic and like it will be rather complicated (especially because I have no idea about compiling 32bit code on a 64bit machine.

Any help would be greatly appreciated, thanks in advance,
Tom

---

### Post by tomscl on 2007-06-29
I've come somewhat further with this now, I've created a 32 bit chroot and aplay now works (I had to make sure the PULSE_SERVER environment variable got passed through in order for it to work), however none of my applications work for various reasons...

When I access a webpage with flash I get or start skype I now get...

*** PULSEAUDIO: Unable to create stream.

several times followed by...

*** PULSEAUDIO: Unable to connect: Connection terminated

I think this is an improvement but still not quite there...onwards and upwards tho :D

---

### Post by JonathanRRogers on 2007-12-30
You may be encountering the issue mentioned in the [PulseAudio Wiki]("http://www.pulseaudio.org/wiki/PerfectSetup#FlashPlayer9"), which is separate from the 32-bit compatibility. It seems that FlashPlayer9's libasound2 usage is buggy, so there's a workaround. I built the workaround module, but am running amd64 Hardy, which still lacks a lib32asound2-plugins package. So, next I need to try running the Flash plugin in a 32-bit chroot like you have or installing the 32-bit libs from some source.

---

### Post by JonathanRRogers on 2007-12-30
I have succeeded in getting the Flash Plugin 9 to play audio through my local PulseAudio server, but it wasn't pretty. I had to build pulseaudio and the experimnetal libflashsupport.so in a 32-bit Gutsy chroot as well as manually copy several shared libraries from i386 Ubuntu packages. I now intend to figure out how to build 32-bit compat packages properly.

---

