---
title: "GTA San Andreas - Sound Stops After A While"
date: 2012-04-06
forum: Wine
---

### Post by mtdewd on 2012-04-06
Been searching for a while, not finding anything similar. 

I'm using Ubuntu 11.10, and when playing GTA San Andreas, the sound just goes dead. Seems to be random, sometimes it will work for 10-15 minutes, sometimes only 1 or 2 minutes. I installed it when using Ubuntu 11.04, and never had this problem. I didn't play the game for some time after upgrading to 11.10, so I can't say for sure if it is specifically the 11.10 version that caused it to stop working.

I have attempted any and all "fixes" that I have found regarding any sound issues other people have experienced. I have tried various Wine config setting changes. Tried full screen and virtual desktop modes. Tried different sound quality settings. I've looked through all the log files I can think of, and can't find anything obvious.

I ran it from the console, and got 2,000+ lines of this before the sound quit:

fixme:d3d:resource_check_usage Unhandled usage flags 0x8.

And then the last line of output was this, which doesn't show up until I exit the game:

fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
err: xvidmode:ComputeGammaFromRamp low-biased gamma ramp (1015), rejected

No output is generated at the time when the sound stops working.

Sound card is SB X-Fi Xtreme Audio

Any suggestions? What can I do to help with diagnosis?

---

### Post by mtdewd on 2012-04-26
Any thoughts on this? Suggestions on how I might diagnose it?

---

### Post by DoktorSeven on 2012-04-26
I get audio issues on a lot of things running in Wine if I keep PulseAudio installed and used.  Myself, I just completely uninstall and disable PA from my system, but you can temporarily disable it by prefixing the wine command with **pasuspender** ([http://askubuntu.com/questions/8425/how-to-temporarily-disable-pulseaudio](http://askubuntu.com/questions/8425/how-to-temporarily-disable-pulseaudio))

---

### Post by mtdewd on 2012-04-27
Hey, I appreciate the help! The pasuspender idea didn't work, it turned up all sorts of odd errors, and the game froze at the first screen where the sound started. So I just created the client.conf and put in the "autospawn = no" line and then killed pulseaudio. I just killed 2 hours of my life playing the game with no problems! Finally. Thanks again!

---

### Post by aasami on 2012-08-20
I suffer from this too, and haven't found  solution yet.

According to [_wine wiki_]("http://wiki.winehq.org/Sound") it is due to bug in either wine or pulseaudio or alsa plugin.

There is a [_bug report_]("https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/805940") opened against this issue, so I hope it will get fixed soon.

If some of you will have luck in resolving this issue please let us all know.
Thank you and regards,

Aas.

---

### Post by mtdewd on 2012-08-20
I have upgraded to ubuntu 12.04, and am using lastest version of Playonlinux, with GTA installed using Wine 1.3.30. 

In the audio tab of wine configure, I set the Output Device and Voice Output Device to "HDA Creative - digital" (my soundcard) instead of "system default" (which, I presume, would use Pulse Audio). I assume this effectively by-passes Pulse Audio? Anyway, since making these changes, I have not had any further problems with the sound, and I no longer have to kill pulse audio each time I play.

---

