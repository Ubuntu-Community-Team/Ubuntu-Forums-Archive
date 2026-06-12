---
title: "No Audio in 8.10 64-bit"
date: 2009-01-08
forum: x86 64-bit Users
---

### Post by Phobos23 on 2009-01-08
I used to have no problems with Ubuntu 8.04, 64-bit.  When I made a clean install of 8.10, I consistently had and still have no audio.

I have reinstalled the alsa-base and stopped and restarted alsa.

See below:
root@eric-laptop:/home/eric# sudo /etc/init.d/alsa-utils stop
 * Shutting down ALSA...                                                 [ OK ] 
root@eric-laptop:/home/eric# sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/eric/.gvfs
      Output information may be incomplete.
Terminating processes: 5370 5514lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/eric/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/eric/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/eric/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-atiixp-modem snd-atiixp snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-atiixp-modem snd-atiixp snd-ac97-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
root@eric-laptop:/home/eric# sudo /etc/init.d/alsa-utils start
 * Setting up ALSA...                                                    [ OK ] 


Still, I have no audio.  My hardware is detected as:

card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I did notice that I had an alsa package that was labeled as 32-bit installed called "lib32sounda" as well as the standard "libsounda" package.  Could this have something to do with it?

---

### Post by pussinboots on 2009-01-11
I had a similar experience (upgrade to 8.10 killed my audio, I'm also using 64-bit).  Turned out a switch to OSS fixed sound for me:

[INDENT][https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)[/INDENT]

I also have an ATI sound card:

[INDENT]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)[/INDENT]

From what I've read, the problem may be specific to these ATI SBx00 cards...

Cheers,

Jason

---

