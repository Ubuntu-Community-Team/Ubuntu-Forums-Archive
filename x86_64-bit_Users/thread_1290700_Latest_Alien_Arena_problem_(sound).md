---
title: "Latest Alien Arena problem (sound)"
date: 2009-10-13
forum: x86 64-bit Users
---

### Post by phatbastard on 2009-10-13
paul-desktop:~/trunk$ ./crx
using /home/paul/.codered/data1/ for writing
using /home/paul/.codered/arena/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy


Won't start.

---

### Post by nzadLithium on 2009-10-14
thats probly caused by either a soundserver mess, pulseaudio or both :D

first thing to try is sudo killall pulseaudio

If that doesnt work try this:
echo "crx.sdl 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "crx.sdl 0 0 disable" > /proc/asound/card0/pcm0c/oss

---

### Post by Yellow Pasque on 2009-10-14
It looks like OpenAL is trying to use oss output. Configure it for ALSA: [http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4309](http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4309)
[http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_OpenAL_for_PulseAudio](http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_OpenAL_for_PulseAudio)

---

### Post by CheatCat on 2009-10-17
I don't really understand what I should do. :sad: They said "set the cvar, s_device, in the console,or in your autoexec.cfg" How I set the cvar in the console? :? And what about the autoexec.cfg? I don't find any such file.

EDIT: It was two links, I haven't look at the wiki yet! xD

EDIT²: Nope, I tried to edit the /etc/openal/alsoft.conf file and remove all drivers except pulse. And I still get errors..

---

### Post by nzadLithium on 2009-10-18
you can't set it in the consol coz the game won't start.

The autoexec.cfg doesnt exist unless you create it. I wouldnt bother. The problem seems to be something that influences the startup of the game its unlikely it would have loaded the cfg in that time. I would supply it as a command line parameter. go to the terminal type alien-arena +set (variable name) value

the s_device parameter doesn't exist. I checked just now.

in your alien arena folder where crx is do you see crx.sdl? try running that one, its what the alien-arena script makes my pc do.

---

### Post by CheatCat on 2009-10-22
No, I don't see any crx.sdl file.. :(

---

### Post by nzadLithium on 2009-10-23
I'll take it you didnt install from synaptic then.

How did you install it?

---

