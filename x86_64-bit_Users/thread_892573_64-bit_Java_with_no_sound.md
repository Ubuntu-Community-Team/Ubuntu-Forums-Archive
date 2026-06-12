---
title: "64-bit Java with no sound"
date: 2008-08-17
forum: x86 64-bit Users
---

### Post by MindFlayer on 2008-08-17
Hello,

As the topic says, I'm having a problem with 64-bit Ubuntu and Java. I have set up pulseaudio according to [this]("http://ubuntuforums.org/showthread.php?t=714712") guide and now the sound is working in just about every place (SDL, flash, ALSA, etc.) except not in Java programs or applets.

Has anyone got any ideas where to start debugging this? The java runtime I'm using is openjdk-6-jre. Could you tell me if A) you have the sounds working in 64-bit Java, B) which JRE are you using? and C) Did you do anything special to get it to work? Thanks a lot!

---

### Post by Thelasko on 2008-08-18
> The java runtime I'm using is openjdk-6-jre
Ok, the two versions of Java that work are:

**OpenJDK-6** mostly works with some bugs, the only 64-bit version of Java that will work with Firefox.

**Sun-Java** this has no plugin for Firefox, and therefore won't work with applets.  It should work fine with Java programs.

[From this page]("http://openjdk.java.net/groups/sound/"), Sun didn't release the source code for sound in Java.  Therefore the OpenJDK team is developing it on their own.  I haven't tried it personally and I will let you know if it works on my machine when I get a chance to try it (I'm at work now).

Do you have a link to a website that uses sound in Java so I may try it on my machine?

---

### Post by MindFlayer on 2008-08-18
Interesting, so that could explain why the openjdk doesn't have sounds yet. I guess I'll try again with sun-java to see if it makes any difference. I don't necessarily need applets yet (although it'd be ideal if the sound would work in both naturally).
 
> Do you have a link to a website that uses sound in Java so I may try it on my machine?
Here's one for example:
[http://www.realapplets.com/tutorial/SoundExample.html](http://www.realapplets.com/tutorial/SoundExample.html)

---

### Post by IntuitiveNipple on 2008-08-18
I have sound output from OpenJDK/JRE 6 on amd64 with applets. I tested the sound applet you linked to.

The sound isn't being routed through pulse-audio though.

There appears to be work going on in OpenJDK currently adding support for pulse-audio, judging by recent patches in the mailing-list.

---

### Post by Thelasko on 2008-08-19
I have pulse-audio and OpenJDK and it worked for me.  If you run the program from the command line, what's the output?

---

### Post by MindFlayer on 2008-08-19
I've attached the output of firefox in this post, but I didn't see anything particularly suspicious in it.

Another thing I'm worried is that when I do "speaker-test -c6", I get this: ```
speaker-test: *** PULSEAUDIO: Unable to create stream.
Unable to set hw params for playback: Input/output error
Setting of hwparams failed: Input/output error
pcm_pulse.c:115: pulse_stop: Assertion `pcm->stream'  failed.
```
 but when I do "speaker-test -c6 -Dpulseaudio", it works fine.

It looks like the default alsa device might be wrong or something like that, but I don't know why everything else is working fine then. :confused:

---

### Post by Thelasko on 2008-08-19
There was a [bug report]("https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/221673/+viewstatus") with the same error.  It has been fixed.  Is your system up to date?

P.S. Nothing out of the ordinary in that text file.  I think it's a pulse audio problem.

---

### Post by MindFlayer on 2008-08-19
My system is Ubuntu Hardy using the latest packages from hardy-proposed and hardy-backports. alsa-base seems to be 1.0.16-0ubuntu4 but libasound2 is indeed still at 1.0.15-3ubuntu4.

Guess I'll have to wait for the fix to arrive for Hardy, then see if that fixes it (or compile it myself).

---

### Post by Thelasko on 2008-08-19
Oops!  I just went back and reread your first post.  You have 5.1 surround enabled.  That's likely the only difference between your system and mine.  Try repeating step 5 of that HOWTO you linked to.  Make sure Java is using pulse audio.  If it is, and it still doesn't work, try setting it to Alsa (or whatever flash uses).  My guess is that Java doesn't support 5.1 channels.

If you have all of the updates for Hardy, it makes no sense that your Java doesn't have sound and mine does.  It has to be the surround sound.

---

