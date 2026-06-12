---
title: "Sacrificies to the Recent jaunty update that p4wnd my sound..."
date: 2009-06-26
forum: x86 64-bit Users
---

### Post by tixetsal on 2009-06-26
A recent (the past week) jaunty update p4wned my audio.  I tinkered with reinstalling packages, changing group memberships, alsa, salsa, oss, pulse, and cheese-dip and bean burrito.  Heck, I even sacrificed some  small animals to the great jackalope, but I can't figure out what went wrong.  
I was not sure what the catalyst was, so I reinstalled.  The sound worked great until my first update and reboot, so it is definitely related to an update, though I am not sure which one.
I am running 9.04 amd64 on a ECS GF8200A (V1.0) ATX AMD Motherboard with HDMI Audio turned ON in the BIOS, although the audio I am referring to is desired from the audio jack in the back of the computer (not sure if the HDMI BIOS option is a factor), and I switched the video feed over to DVI because I thought that maybe using HDMI was "confusing" the kernel.
Before I reinstalled the only device that would show up was the HDMI audio out, now aplay -l yields this message:

shaun@brpc:~$ aplay -l
aplay: device_list:217: no soundcards found...

My volume control options seem to be much more limited than they were before the updates.  I'm going to try reinstalling with the HDMI audio BIOS switch turned off, but I have no guarantee that this will remedy this issue.  I am grasping straws...

Meh!

---

### Post by tixetsal on 2009-06-27
I discovered that by booting 2.6.28-11-generic, instead of 2.6.28-13, my audio was restored, as long as I booted that kernel. I have another box with Asus P5N7A-VM MOBO, and this bug did not effect that machine. My AMD geforce 8200 will not play nice with 28-13 though. My sound card shows up in lspci, but aplay -l tells that I have no sound card.

---

### Post by tixetsal on 2009-07-24
Sound was miraculously restored about 2 weeks ago, in the newest kernel, even before all of the PulseAudio updates rolled out. I did install some codecs for multithreaded encoding / decoding around that time, but I'm not sure if it was an update or my own accidental tinkering resolving the problem.

It was either the hand of God, or the developers are listening.

---

### Post by gshockxc on 2009-08-03
> **tixetsal said:**
> A recent (the past week) jaunty update p4wned my audio.  I tinkered with reinstalling packages, changing group memberships, alsa, salsa, oss, pulse, and cheese-dip and bean burrito.  Heck, I even sacrificed some  small animals to the great jackalope, but I can't figure out what went wrong.  
I was not sure what the catalyst was, so I reinstalled.  The sound worked great until my first update and reboot, so it is definitely related to an update, though I am not sure which one.
I am running 9.04 amd64 on a ECS GF8200A (V1.0) ATX AMD Motherboard with HDMI Audio turned ON in the BIOS, although the audio I am referring to is desired from the audio jack in the back of the computer (not sure if the HDMI BIOS option is a factor), and I switched the video feed over to DVI because I thought that maybe using HDMI was "confusing" the kernel.
Before I reinstalled the only device that would show up was the HDMI audio out, now aplay -l yields this message:

shaun@brpc:~$ aplay -l
aplay: device_list:217: no soundcards found...

My volume control options seem to be much more limited than they were before the updates.  I'm going to try reinstalling with the HDMI audio BIOS switch turned off, but I have no guarantee that this will remedy this issue.  I am grasping straws...

Meh!

I've had exactly the same problem with my sound.  I wasn't able to trace it back as far as you did, but I was able to narrow down the date that the update occurred.  I thought it was tied to the PulseAudio updates, so I removed those, but it didn't help.  Based on what you said worked for you, I'm going to try and boot the older kernel and see if that works.  I keep getting the same messages as you saying that my sound card does not exist.

---

