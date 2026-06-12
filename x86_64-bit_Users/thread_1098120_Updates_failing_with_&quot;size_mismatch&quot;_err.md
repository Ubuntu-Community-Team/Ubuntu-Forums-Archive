---
title: "Updates failing with &quot;size mismatch&quot; error"
date: 2009-03-16
forum: x86 64-bit Users
---

### Post by Dark Angel on 2009-03-16
I'm trying to install updates that came in this morning (17th March '09) but am getting these errors:

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.2_amd64.deb)
  Size mismatch


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.2_amd64.deb)
  Size mismatch


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat1d_0.cvs20070307-5ubuntu7.2_amd64.deb)
  Size mismatch


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.2_amd64.deb)
  Size mismatch


I have tried both the Main server and the server for Australia but both do the same thing.

I've also tried everything suggested in this thread: [http://ubuntuforums.org/showthread.php?t=1011290&highlight=update+failing+size+mismatch]("http://ubuntuforums.org/showthread.php?t=1011290&highlight=update+failing+size+mismatch") but it hasn't worked.

Anyone have any suggestions?

---

### Post by bodhi.zazen on 2009-03-16
This has been reported and is being worked on.

Rumor is it should be fixed by tomorrow (if not sooner).

---

### Post by Dark Angel on 2009-03-16
Thanks. :D I'll keep my eyes open.

---

### Post by mdr on 2009-03-17
yeah I got this too this am (17th) in Australia using the internode mirrors.

did an apt-get update and they installed fine.

however - now my box will not boot - gets stuck on configuring interfaces ...

but that I guess is another story.

---

### Post by Dark Angel on 2009-03-17
Ok, updates went through fine this morning.  Thanks. :D

---

