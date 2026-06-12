---
title: "32 bit aoss sound on a 64 bit system, the Odyssey continues"
date: 2007-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Alpinist on 2007-07-13
At this date and time I'm hardly poineering 64 bit systems but still looks like Linux is not quite ready for prime time in the 64 bit arena.

I have recently installed 64 bit Kubuntu on an AMD 64 dual core system.  Overall things are running fairly smoothly but sill have one issue left in getting sound configured and wanted to post my steps for others as I did a lot of searching to get this far.

Tried to get sound working in Cedega and Teamspeak.  Teamspeak only uses OSS for sound and is a 32 bit app, so to get it working requires the 32 bit version of alsa-oss.  No problems with that.  Can run Teamspeak and it functions correctly.

Ok, in Cedega I was noticing I can only get sound when I set it to OSS and not when I try to use alsa.  It's nice that I can at least get sound, but of course with oss only a cedega game or teamspeak can have sound but not both at once.

Turned out I needed lib32asound.  Got that installed and Cedega works with alsa.  Even verified I can hear sound from a Cedega game and XMMS at the same time.   Great.  

Now all I have to do is start teamspeak with artsdsp or aoss and I can have sound from both.  Hmm, not working.  Start up Teamspeak from a command line to see what is going on.  If I try to start it from aoss I get ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.    If I try to start TS with artsdsp I get a similar error ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.

This is another 32 bit problem.  I need a 32 bit version of aoss.  Kilz posted a package link in the Ubuntu forums.  [http://ubuntuforums.org/archive/index.php/t-425327.html](http://ubuntuforums.org/archive/index.php/t-425327.html).  Installed his package and I can bring up Teamspeak with aoss and hear people talking and hear game sound at the same time.

Problem is now the microphone shows up as muted. Doesn't seem to be recognized.  So I can run TeamSpeak without aoss and it works perfectly but I can't hear sound from any other program.  Or I can run TS with aoss and hear everything but can't talk to anybody.

If anyone can provide suggestions that will get the mike working wtih 32 bit libaoss.so I would appreciate the input.

---

### Post by go_beep_yourself on 2008-03-23
Did you try to compile with linux32?

---

### Post by go_beep_yourself on 2008-03-28
I'm trying to accomplish the exact same thing as you. Compiling with linux32 still gives 64 bit binaries. What needs to be done is gcc flags set to -m32. I'm still looking for the correct variable to set for make to do that. Maybe I'll take a look inside a makefile.

---

