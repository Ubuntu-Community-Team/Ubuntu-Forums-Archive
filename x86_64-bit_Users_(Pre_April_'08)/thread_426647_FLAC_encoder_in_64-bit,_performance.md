---
title: "FLAC encoder in 64-bit, performance?"
date: 2007-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fraoch on 2007-04-28
Hi, just put together a new system with an Intel Core 2 Duo E6600 and installed 7.04 64-bit on it today!

I'm installing and configuring all the software, basically trying to get it looking and running how I want.  So far so good, although I haven't tested everything out yet, there's nothing broken so far.  Despite the theoretical extra memory required for 64-bit, I haven't run into slowdowns caused by my reuse of 512 MB of old memory, and I'll be upgrading it to 2 GB in a year or so.  Special thanks to SD-Plissken and Kilz, whose posts convinced me it wouldn't be all that hard if I followed instructions.:) 

Why do I want or need 64-bit?  Well, first, because I can.  This is the first really powerful hardware I've ever owned, I want to take full advantage.  Secondly, obviously, I'm looking for speed increases.  I took a look at this:

[http://ubuntuforums.org/showthread.php?t=318743](http://ubuntuforums.org/showthread.php?t=318743)

which convinced me there are speed increases to be had.  The most processor-intensive thing I'll be doing will be audio encoding to MP3 and FLAC plus some MP3Gain work.  I note that MP3 encoding oddly was a little slower in those benchmarks, but that FLAC encoding is not listed.  I figure FLAC and MP3Gain are pretty mathematically-intensive, there ought to be gains.  I compress FLAC at -8, which takes probably 2 minutes per CD track on my temporary 1.2 GHz Duron PC and 1 minute on my former Pentium 4 2.8 GHz machine.  MP3Gain is also pretty processor-intensive in all cases.

Has anyone used the FLAC encoder in 64-bit?  Does it run any faster?

I'll do some tests but the only 32-bit machine I have to compare is the Duron.  I know without even checking that the E6600 will cream it, 64-bit or not, so it's not a valid comparison.

---

### Post by Fraoch on 2007-05-18
Well, I'm not sure if 64-bit flac is faster than 32-bit, but it sure isn't slow on this machine: 10-15 seconds per CD track!  Whoa!:guitar:

---

### Post by david_2001 on 2007-05-18
Just for fun:

Input file, ripped from a cassette tape a little while ago: 
> -rw-rw---- 1 david david 119181356 2005-09-27 23:09 01 Bags Groove Take 1.wav

**FLAC**
Command:
```
date && flac -8 -o test.flac 01\ Bags\ Groove\ Take\ 1.wav && date
```
64-bit:
> Fri May 18 23:55:07 BST 2007

flac 1.1.2, Copyright (C) 2000,2001,2002,2003,2004,2005  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

options: -P 4096 -b 4608 -m -l 12 -e -q 0 -r 0,6
01 Bags Groove Take 1.wav: wrote 68140295 bytes, ratio=0.572

Fri May 18 23:56:03 BST 2007
32-bit in chroot environment:
> Fri May 18 23:57:08 BST 2007

flac 1.1.2, Copyright (C) 2000,2001,2002,2003,2004,2005  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

options: -P 4096 -b 4608 -m -l 12 -e -q 0 -r 0,6
01 Bags Groove Take 1.wav: wrote 68140690 bytes, ratio=0.572

Fri May 18 23:58:02 BST 2007
Result: 32-bit comes out 2s ahead.  Don't know why the output file from the 64-bit encoder is very slightly smaller.

**OGG**
Command:
```
oggenc -o test.ogg 01\ Bags\ Groove\ Take\ 1.wav
```
64-bit:
> Opening with wav module: WAV file reader
Encoding "01 Bags Groove Take 1.wav" to 
         "test.ogg" 
at quality 3.00
        [ 99.9%] [ 0m00s remaining] \ 

Done encoding file "test.ogg"

        File length:  11m 15.0s
        Elapsed time: 0m 49.5s
        Rate:         13.6620
        Average bitrate: 100.5 kb/s
32-bit in chroot environment:
> ening with wav module: WAV file reader
Encoding "01 Bags Groove Take 1.wav" to 
         "test.ogg" 
at quality 3.00
        [ 99.9%] [ 0m00s remaining] \ 

Done encoding file "test.ogg"

        File length:  11m 15.0s
        Elapsed time: 1m 00.5s
        Rate:         11.1592
        Average bitrate: 100.5 kb/s
Result: 64-bit wins by 11s.  File sizes were 8490161 bytes for the 64-bit encoder and 8490125 bytes for the 32-bit.

---

### Post by Fraoch on 2007-05-18
David: very interesting and it adds to those benchmarks I posted which said that LAME was slower in 64-bit while ogg was faster.  Looks like flac is in the LAME camp, or at the very least there are no significant speedups to be had.

The file size difference is worrisome for those who go to great lengths for bit-perfect ripping and encoding, although it's only a few hundred bytes.

---

### Post by feld on 2007-05-19
64bit doesnt mean faster just because it's now 64bit. in fact in some ways it is slower.

the advantage? 64bit addressing and more ram available. Otherwise you're probably better off running 32bit.

People can argue left and right but the facts are the facts -- 64bit has some drawbacks. Any decent programmer could elaborate on this subject. I can remember a particular example given by someone in the Gentoo community but I'm too lazy to go look it up.

Anyway, don't just use 64bit unless you have a specific reason to. 

My reason? 4GB of ram.


PS the situations that make it slower probably wont be noticable for you; just wanted to make it clear to you that just because 64 > 32, it isn't better in _every_ possible way.

---

### Post by John.Michael.Kane on 2007-05-19
> **feld said:**
> 64bit doesnt mean faster just because it's now 64bit. in fact in some ways it is slower.
No one in this part of the forum has ever said that 64bit was the golden ticket to speed,


> **feld said:**
> the advantage? 64bit addressing and more ram available. Otherwise you're probably better off running 32bit.
Theres many reasons for the use of 64bit, and addressing more ram is only one reason.


> **feld said:**
> People can argue left and right but the facts are the facts -- 64bit has some drawbacks. Any decent programmer could elaborate on this subject. I can remember a particular example given by someone in the Gentoo community but I'm too lazy to go look it up.
Almost everyone that runs 64bit understands theres drawbacks, and that gains can be minor or significant depending on the task.

> **feld said:**
> Anyway, don't just use 64bit unless you have a specific reason to.
And the people here who run it have their reasons. Which may not be the reason you feel they should run 64bit.

> **feld said:**
> My reason? 4GB of ram.
Thats your reason. that however is not the only reason to use it.


> **feld said:**
> PS the situations that make it slower probably wont be noticable for you; just wanted to make it clear to you that just because 64 > 32, it isn't better in _every_ possible way.
Most who come here to ask about 64bit use, are told that certain tasks done in a 64bit environment may not show any noticeable effects in either way.

Also no one ever said it was better in every way. 64bit users give new users their opinions. They also have access to a list of threads that debated the issue. This allows them to form their own conclusion.

---

### Post by ronocdh on 2007-05-19
Very cool post, David_2001. Thanks a lot for taking the time! I still bleed 64-bit, but it's nice to see hard figures on its performance.

---

### Post by david_2001 on 2007-05-19
One more, just for fun.  This time the exercise is ripping a title from a DVD to mpeg4 video/mp3 audio using mencoder.  The title is the Fruity Oaty Bar Easter Egg from the Serenity DVD and is 1:38 duration.  Note that I ran the rip a couple of times before taking the timings so that mencoder was reading from cache memory and not from the disk.

Command:
```
date && mencoder dvd://18 -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=5000 -oac mp3lame -lameopts br=128 -quiet -o test.avi && date

```
**64-bit:**> Sat May 19 21:32:37 BST 2007

MEncoder 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
There are 22 titles on this DVD.
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: en
number of subtitles on disk: 1
success: format: 0  data: 0x32D8E000 - 0x3656c000
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
[V] filefmt:2  fourcc:0x10000002  size:720x576  fps:25.00  ftime:=0.0400

[Cut]

Video stream: 4698.405 kbit/s  (587300 B/s)  size: 57649435 bytes  98.160 secs  2461 frames

Audio stream:  208.423 kbit/s  (26052 B/s)  size: 2557344 bytes  98.160 secs

Sat May 19 21:33:44 BST 2007

**32-bit in chroot environment:**> Sat May 19 21:37:48 BST 2007

MEncoder 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 2.80GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

[Cut]

Video stream: 4702.126 kbit/s  (587765 B/s)  size: 57648066 bytes  98.080 secs  2461 frames

Audio stream:  208.438 kbit/s  (26054 B/s)  size: 2557536 bytes  98.160 secs

Sat May 19 21:39:00 BST 2007
**Result**: 64-bit wins by 5s (01:07 vs 01:12).  File sizes are 60369154 bytes for the 64-bit encoder and 60367924 bytes for the 32-bit.

---

