---
title: "WineAsio + Jack + Audio Interface = Not Working"
date: 2016-02-27
forum: Wine
---

### Post by christian45 on 2016-02-27
I haven't been able to get my Audio Interface to work with my DAW Ableton Live. I can't get sound out of it, and I can't put sound into it. Check out my image attachment to see if I am doing anything wrong?

1. I installed Ableton Live through PlayOnLinux
2. I installed WineASIO on Ableton through PlayOnLinux 
3. I installed Jack and I think I put the right settings for my Audio Interface.
4. When I go to Ableton and select ASIOS - WineAsio, I start to hear a small crackling in my headphones.
5. When I load an instrument, and I hit a note, a loud never stopping beep goes off. 

I am using Ableton Live Suite 9 32-bit on Linux Mint 17 with a M-Audio M-Track USB Audio Interface. Here is the steps I took.

Am I doing anything wrong?

If you don't have an answer, you have any idea where I can ask this question and perhaps get an answer? I've had this problem for a while. 
I haven't been able to ditch windows completely because of this issue.

---

### Post by marseille2 on 2016-02-29
[Yoshi](http://ubuntuforums.org/member.php?u=1971531), seems to know a lot about using wine-hq for linux audio. A few weeks ago, he posted an [informal guide](http://ubuntuforums.org/showthread.php?t=2309922) about it. The interesting thing is that Yoshi doesn't use  Jackd ... only wine and pulseaudio (PA). He even mentions how to get better latency from PA by changing a few lines of code in /etc/pulse/daemon.conf and /etc/pulse/default.pa. ... Another tip you might want to check out, is the special RT (realtime) version of Wine-HQ. It's located in the KX-studio repositories.

---

