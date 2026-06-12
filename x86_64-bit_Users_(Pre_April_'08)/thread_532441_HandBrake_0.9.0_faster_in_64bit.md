---
title: "HandBrake 0.9.0 faster in 64bit"
date: 2007-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by stmiller on 2007-08-22
I compiled a 64bit Linux binary of the latest 0.9.0 release of HandBrake, and did a quick test vs. 32bit Windows on my dual booting machine. If you are interested, here are the results:

HandBrake 0.9.0
Test file: 32:23 title from a DVD iso image.
Encoding with 2 pass h.264, quality 0.5, resulting in a 134MB mp4 video.

**Windows XP 32bit:**
HandBrakeCLI.exe -i file.iso -o file.mp4 -t 2 -e x264 -q 0.5 -2 -T
[B]Pass 1: 69.07 FPS avg
Pass 2: 46.97 FPS avg[/B]
[B]
Kubuntu Linux 64bit:[/B]
HandBrakeCLI -i file.iso -o file.mp4 -t 2 -e x264 -q 0.5 -2 -T
[B]Pass 1: 84.64 FPS avg 
Pass 2: 54.92 FPS avg
[/B]

---

