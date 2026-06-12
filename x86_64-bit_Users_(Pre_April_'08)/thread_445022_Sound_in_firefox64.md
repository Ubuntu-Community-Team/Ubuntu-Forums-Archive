---
title: "Sound in firefox64"
date: 2007-05-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by the_it on 2007-05-15
I followed Kilz's guide to get flash with sound, and java working on my firefox64.  Everything seems to be just as he said but...

firefox itself can't get any sound.  I think this is separate from plugins.  Basically, a site like meebo doesn't give me sound (which is I think just javascript ajax).  The plugins themselves probably know how to play fair with the soundcard/mixer and all, but maybe the browser doesn't?  This seems counter-intuitive to me.

Running Ubuntu Feisty Fawn 7.04 AMD64, with mozilla firefox (from repos) 2.0.0.3+1-0ubuntu2.  It's got to be the 64bit one because it's the one that came out of the box, and i used the nsplugin wrapper script to install flash and stuff.

So yeah, whick files do I poke around?

---

### Post by Kobalt on 2007-05-15
Make sure you have the *lib32asound2* package installed (in Synaptic) first. If it's not there, install it. Then modify the following file : ```
gksu gedit /etc/firefox/firefoxrc
```
Change the line > FIREFOX_DSP="none" with this one > FIREFOX_DSP="aoss"

---

### Post by the_it on 2007-05-16
Thanks! worked perfectly.  Must've missed that.

---

### Post by JAmerican on 2007-06-30
Didn't fix my issue. I am in the same boat. AMD64 Fiesty with Firefox out of box version. 

My music works great and so does my video sound. Flash is left. The NSPluginwrapper enabled video for Firefox but no sound. Please help.

JAmerican

---

### Post by Snyper64 on 2007-06-30
Didn't work for me either, is it possible to make it work with ALSA instead since I have a sound profile setup(asoundrc) for my optical output on my USB soundcard?

---

### Post by JAmerican on 2007-06-30
Do your audio work now with videos and music?

If you are just having Flash issues, what I did was reinstalled the root partition of Ubuntu and used the nspluginwrapper without messing with any ALSA libraries. Read through here and see if you are in the same boat...

[http://ubuntuforums.org/showthread.php?t=487167](http://ubuntuforums.org/showthread.php?t=487167)

JAmerican

---

### Post by Snyper64 on 2007-06-30
My sound works fine with videos and music online, its just flash videos that I am having problems with. Also I needed to setup which hardware device my sound uses since I go through an optical out that can also be used as a standard 2.5mm headphone jack for on the go(Turtle Beach Audio Advantage Amigo) that it wants to use by default.

---

