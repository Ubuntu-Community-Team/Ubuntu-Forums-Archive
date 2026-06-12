---
title: "This is why I stay with AMD64"
date: 2005-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by HankB on 2005-12-20
In a 32 bit chroot:
```
(chroot)hbarta@baobab:~/$  time toolame -b 128 prairie.wav prairie.mp3
Parsing Wave File Header
>>> 22.05 kHz Sampling freq selected
>>> Input Wave File is Mono
--------------------------------------------
Input File : 'prairie.wav'   22.1 kHz
Output File: 'prairie.mp3'
128 kbps MPEG-2 LSF Layer II single-ch Psycho model=1  (Mode_Extension=0)
[De-emph:Off    Copyright:No    Original:No     CRC:Off]
[Padding:Normal Byte-swap:Off   Chanswap:Off    DAB:Off]
--------------------------------------------
Insufficient PCM input for one frame - fillout with zeros
Hit end of audio data
Avg slots/frame = 835.918; b/smp = 5.80; bitrate = 128.000 kbps

Done

[B]real    1m57.246s
user    1m53.424s
sys     0m2.062s[/B]
(chroot)hbarta@baobab:~/
```
and in 64 bit:
```
hbarta@baobab:~/$ time toolame -b 128 prairie.wav prairie.mp3
Parsing Wave File Header
>>> 22.05 kHz Sampling freq selected
>>> Input Wave File is Mono
--------------------------------------------
Input File : 'prairie.wav'   22.1 kHz
Output File: 'prairie.mp3'
128 kbps MPEG-2 LSF Layer II single-ch Psycho model=1  (Mode_Extension=0)
[De-emph:Off    Copyright:No    Original:No     CRC:Off]
[Padding:Normal Byte-swap:Off   Chanswap:Off    DAB:Off]
--------------------------------------------
Insufficient PCM input for one frame - fillout with zeros
Hit end of audio data
Avg slots/frame = 835.918; b/smp = 5.80; bitrate = 128.000 kbps

Done

[B]real    1m28.411s
user    1m24.960s
sys     0m1.992s[/B]
hbarta@baobab:~/$

```

That's a 33% bump from 32 bit to 64 bit. (My understanding is that something like this will run the same speed in a 32 bit chroot as in a 32 bit system.

Otherwise, the 64 bit system is a royal pain. Apps in a 32 bit chroot are not seamless. (No sound for flash. No printer support) I can probably get these working if I work with it. But my hobby is not twiddling with the system to get everything to work. :( Linux at best still takes some twiddling (as compared to pre-installed Windows.) But AMD64 takes even more.

<sigh>

---

