---
title: "Sound screwup"
date: 2008-05-16
forum: x86 64-bit Users
---

### Post by Peior Crustulum on 2008-05-16
Hi everyone!

I just tried the latest X-Fi driver from creative and naturally failed miserably:(
I've installed OSS 4.0 in the process and it did not work either.

So after an hour of trying again and again, I gave up and simply put inn my old mobo sound card (the one that comes with the Striker Extreme).

When I start up my computer I get the startup sound and the login sound, but that's as far as things go soundwise.
I can't listen to music, or hear anything when playing a movie.
My system is completely soundless save the startup and login sound.

What did I do to screw this up, and how do I fix it :confused:

I really appreciate any help you can give me, thanks beforehand!

Edit: 8.04 AMD64 of course :)

---

### Post by Yellow Pasque on 2008-05-16
See the OSS4 guide in my signature (I suggest following the link at the bottom of the post on removing a failed install and starting over). If you still have questions, let us know.

---

### Post by Peior Crustulum on 2008-05-16
I just get this message when I try to save the changes to the status file.

> You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

How do I get full access?

Thanks for the reply :)

Edit: never mind, found out how.

Edit2: I get this now > Selecting previously deselected package oss-linux.
(Reading database ... 113129 files and directories currently installed.)
Unpacking oss-linux (from oss-linux_v4.0-1015_amd64.deb) ...
Setting up oss-linux (v4.0-1015) ...
Building OSS Modules for Linux-unknown 2.6.24-16-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Building module ali5455
Building module allegro
Building module als300
Building module als4000
Building module apci97
Building module atiaudio
Building module audigyls
Building module audioloop
Building module audiopci
Building module cmi8788
Building module cmpci
Building module cs4280
Building module cs4281
Building module digi32
Building module digi96
Building module emu10k1x
Building module envy24
Building module envy24ht
Building module fm801
Building module geode
Building module hdaudio
Building module hdsp
Building module ich
Building module imux
Building module lynxone
Building module lynxtwo
Building module maestro
Building module neomagic
Building module ossusb
Building module riptide
Building module s3vibes
Building module sblive
Building module sbxfi
Building module softoss
Building module solo
Building module sonorus
Building module trident
Building module via8233
Building module via97
Building module vmix
Building module vortex
Building module ymf7xx
depmod -a
-----------------------------
Detected Creative SB X-Fi (EARLY BETA)
Detected Nvidia High Definition Audio (MCP55)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
-----------------------------

Starting Open Sound System
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm_oss is in use
ERROR: Module snd_mixer_oss is in use by snd_pcm_oss
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_pcm_oss
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hwdep is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
Failed to disable conflicting sound drivers
Reboot and try running soundon again

Also check that you have not compiled sound support statically
into the kernel.


Lots of failures there, what do I do?

---

### Post by Peior Crustulum on 2008-05-16
After a reboot it started working just fine, I think I can reinstall the volume control by myself.

Thank you!

---

