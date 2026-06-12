---
title: "X86 Aspire 6920 No Sound :("
date: 2008-12-30
forum: x86 64-bit Users
---

### Post by toyota thundra on 2008-12-30
Hey guys, Im a n00bie here, so I hope my post is in the correct section. As the title says  have no sound with a fresh install on my Acer Aspire. I downloaded WUBI, and dual booted with Vista... I had to get away from Vista, it was a nightmare. So maybe you all can help a new linux user out? Where do I start? 

Josh

---

### Post by neu2buntu on 2008-12-30
maybe try right click on speaker icon on top panel  >choose open volume control >and in playback make sure master pcm and front are not muted (x over speaker) and the volume is up

---

### Post by toyota thundra on 2008-12-30
> **neu2buntu said:**
> maybe try right click on speaker icon on top panel  >choose open volume control >and in playback make sure master pcm and front are not muted (x over speaker) and the volume is up

All good, not muted. God I would've felt stupid had that been the issue. :D Any other thoughts?

---

### Post by neu2buntu on 2008-12-30
amazing how many this has happened to..lol    ok next thing to try goto >system>preferences>sound  and in devices window try alsa and try test button for these to see if it beeps  .....   also open a terminal (>applications >accessories >terminal  ant type in ```
aplay -l 
```and copy and paste the output here in a reply

---

### Post by toyota thundra on 2008-12-30
Believe me i did read the sticky and have been toying with it. (Getting no where) lol This is the response from that:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So now, reboot, check bios, turn on onboard sound?

---

### Post by neu2buntu on 2008-12-30
well its the same type of soundcard as mine ,... no need for reboot or anything yet,.. in that last window >sound preferences in the 5th choice make sure you choose hda intel(Alsa mixer)      and just incase goto speaker icon >right click >open volume control and the device is also hda intel too....




and if still nothing you could open terminal and do command ```
/sbin/alsa force-reload
```  or if it needs root privileges ```
sudo /sbin/alsa force-reload
```
to restart the alsa drivers.....   fingers crossed now!!!

---

### Post by toyota thundra on 2008-12-30
> **neu2buntu said:**
> well its the same type of soundcard as mine ,... no need for reboot or anything yet,.. in that last window >sound preferences in the 5th choice make sure you choose hda intel(Alsa mixer)      and just incase goto speaker icon >right click >open volume control and the device is also hda intel too....




and if still nothing you could open terminal and do command ```
/sbin/alsa force-reload
```  or if it needs root privileges ```
sudo /sbin/alsa force-reload
```
to restart the alsa drivers.....   fingers crossed now!!!
Hmm... You understand this jibberish? :P
 /sbin/alsa force-reload
Terminating processes: 5708.
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
ryski3@ubuntu:~$ sudo /sbin/alsa force-reload
[sudo] password for ryski3: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ryski3/.gvfs
      Output information may be incomplete.
Terminating processes: 5552 7337lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ryski3/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ryski3/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ryski3/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
ryski3@ubuntu:~$

---

### Post by neu2buntu on 2008-12-30
try the second command starting sudo

---

### Post by neu2buntu on 2008-12-30
oops just realised you did that..... ye3ah basically you needed to be sudo to mess with the sound drivers....try playing something to see n ow

---

### Post by toyota thundra on 2008-12-30
NADA. :(   Man where did I put that easy button?

---

### Post by neu2buntu on 2008-12-30
lol....im stumped, but will have a look around to see if i can come up with something for you!!!!    the answer will be out there

---

### Post by toyota thundra on 2008-12-30
I appreciate it. Thanks man. :-k

---

### Post by toyota thundra on 2008-12-30
I went to g00gl3.... and what do ya know? 

[https://bugs.launchpad.net/ubuntu/+bug/218165/comments/17](https://bugs.launchpad.net/ubuntu/+bug/218165/comments/17)

Someone with the same PC, Same issue. 

So Im gonna read through this and try to sort it out. :popcorn:

---

### Post by neu2buntu on 2008-12-30
heres a link that may or may not be usefull...lol...[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
anyway goodluck!!!

---

### Post by toyota thundra on 2008-12-30
ryski3@ubuntu:~$ cd /usr/src
ryski3@ubuntu:/usr/src$ sudo hg clone [http://mercurial.opensound.com/](http://mercurial.opensound.com/) oss-devel
[sudo] password for ryski3: 
requesting all changes
adding changesets
adding manifests
adding file changes

added 595 changesets with 3327 changes to 1337 files
updating working directory
831 files updated, 0 files merged, 0 files removed, 0 files unresolved
ryski3@ubuntu:/usr/src$ 
ryski3@ubuntu:/usr/src$ cd ~/
ryski3@ubuntu:~$ sudo rm -rf oss41build
ryski3@ubuntu:~$ mkdir oss41build
ryski3@ubuntu:~$ cd oss41build/NO_WARNING_CHECKS=yes /usr/src/oss-devel/configure
bash: cd: oss41build/NO_WARNING_CHECKS=yes: No such file or directory
ryski3@ubuntu:~$ makesudo make install
bash: makesudo: command not found
ryski3@ubuntu:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
ryski3@ubuntu:~$ cd ~/
ryski3@ubuntu:~$ sudo rm -rf oss41build
ryski3@ubuntu:~$ mkdir oss41build
ryski3@ubuntu:~$ cd oss41build/sudo make deb
bash: cd: oss41build/sudo: No such file or directory
ryski3@ubuntu:~$ sudo dpkg -i oss*.deb
dpkg: error processing oss*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss*.deb
ryski3@ubuntu:~$ cd /usr/src/oss-devel
ryski3@ubuntu:/usr/src/oss-devel$ sudo hg pull
pulling from [http://mercurial.opensound.com/](http://mercurial.opensound.com/)
searching for changes
no changes found
ryski3@ubuntu:/usr/src/oss-devel$ sudo hg update
0 files updated, 0 files merged, 0 files removed, 0 files unresolved
ryski3@ubuntu:/usr/src/oss-devel$ cd ~/
ryski3@ubuntu:~$ sudo rm -rf oss41build
ryski3@ubuntu:~$ mkdir oss41build
ryski3@ubuntu:~$ NO_WARNING_CHECKS=yes /usr/src/oss-devel/configure
Using the Linux specific script
Error: Current directory must be empty
ryski3@ubuntu:~$ make sudo make install
make: *** No rule to make target `sudo'.  Stop.
ryski3@ubuntu:~$ 

Any advice to what I am doing wrong here?

---

### Post by toyota thundra on 2008-12-30
Im gonna crawl into a hole and cry now.


No rule to make target `install'.

Ive followed the directions to the "T"

---

### Post by toyota thundra on 2008-12-30
Well, I just succsessfully installed OSS 4 from scratch (I think) and this is where im at now:

ryski3@ubuntu:/usr/src$ sudo ossdetect -v
[sudo] password for ryski3: 
Detected Intel High Definition Audio (ICH8)
USB support available in the system, adding USB driver
Detected Generic USB audio/MIDI device (BETA)
ryski3@ubuntu:/usr/src$ 


But it says:

ryski3@ubuntu:/usr/src$ ossinfo -v3
Version info: OSS 4.2 (b 081213/200812310223) (0x00040100) OSS_HG
Hg revision: changeset: 594:f054e739c2bb, tag: tip, date: Wed Dec 31 00:07:02 2008 +0200, summary: Fixed a typo in oss_ich.c
Platform: Linux/x86_64 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 (ubuntu)

Number of audio devices:	0
Number of audio engines:	0
Number of MIDI devices:		0
Number of mixer devices:	0


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 Intel HD Audio interrupts=363 (363)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086284b
    Subvendor ID 0x10250146
     Codec  0: Unknown (0x10ec0889/0x10250146)
     Codec  1: Unknown (0x11c11040)
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices

Audio devices



I have restarted and I AM LOST.... PLEASE HELP ME OUT HERE.:confused:

---

### Post by neu2buntu on 2008-12-31
you must be getting close man,i will not let this sound problem beat me either...lol...we need our music!!!  i will try again 4 u!!   i had problems with recording my output of music i was making in lmms but after about a month or so i found the answer here....so dont give up on it you will get it sorted...ok


it looks like oss4 cant see your soundcard either.....  i think you should stay with alsa and work on it,...did you try my post ,and make sure your alsa is up to date......

---

### Post by toyota thundra on 2008-12-31
So maybe reinstall alsa? <Runs off laughing manically> Where do I start? Ubuntu forum Advanced search.... Yes... Here I go, If nothing else I will know how to install audio stuff well. :D

---

