---
title: "Ubuntu 8.10 on HP HDX 16 - Sound Issue"
date: 2009-10-10
forum: x86 64-bit Users
---

### Post by madmax.santana on 2009-10-10
I have an HP HDX 16 laptop. I had Windows Vista Installed previously. Then I switched to Fedora. Fedora had some repository issues and also i came to know that it is not Fedora, but Ubuntu that is the most popular operating system based on linux.
 Uptil now, Ubuntu has proved no better to me than Fedora! Sadly, but yes. Except for one thing.
 Fedora has some repository issues. Means its yum had some problem configuring networking connections for updates and [ackage installs.
 However one major problem remains the same.
 
 --- SOUND ---
 !!!
 I have just installed Ubuntu and there is no sound. My sound card is correctly installed, I know that.

> 
madmax@Mario:~$ aplay -l
 **** List of PLAYBACK Hardware Devices ****
 card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
   Subdevices: 1/1
   Subdevice #0: subdevice #0
 card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
   Subdevices: 1/1
   Subdevice #0: subdevice #0 			 		



And the speakers are on and alright. Because I have Windows installed in parallel and Windows gives me sound alright.
 Can anyone please suggest what might be the problem with my sound! Please! I don't wanna be switching operating systems! If anyone could please do me a favour and tell me an exact solution for my problem, it would be a great help. Thanks.
 
 P.S. I am using Ubuntu amd64 version!

---

### Post by madmax.santana on 2009-10-10
When i plug in my headphones, the speaker-test app works well and both channels are alright

---

### Post by madmax.santana on 2009-10-10
Problem is now solved....



Thanks to Leprecon!
For anyone having the same problem (only for the mentioned model)
In the shell: type -

> sudo nano /etc/modprobe.d/alsa-base.conf

Now in the end of the file, append this line:

> options snd-hda-intel model=hp-m4

That should definitely solve the problem. If it does not, you have something wrong with your drivers or hardware! Go for extended support. I just know this because of Leprecon, and I am not a Linux Expert... Thanks a lot.

---

