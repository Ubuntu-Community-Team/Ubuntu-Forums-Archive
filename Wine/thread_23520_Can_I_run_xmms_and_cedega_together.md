---
title: "Can I run xmms and cedega together?"
date: 2005-04-02
forum: Wine
---

### Post by seven on 2005-04-02
I have  manages to run xmms and other sound application together by following this guide:
[http://www.ubuntuforums.org/showthread.php?t=8882](http://www.ubuntuforums.org/showthread.php?t=8882)
and it works great.

  but I cant run cedega with xmms. If I start xmms and then launch a game - 
cedega doesn't play anything.

here is the relevant config from cedega's config:
> 
[WinMM]
"Drivers" = "winealsa.drv"
"WaveMapper" = "msacm.drv"
"MidiMapper" = "midimap.drv"

[wineoss]
;"UseMMap" = "Y"
;"FullDuplex" = "N"
;; Specify a mapping for what digital audio devices to use
;"dsp0" = "/dev/dsp0"
;"mixer0" = "/dev/mixer0"

[winealsa]
"UseMMap" = "Y"
;"pcm0" = "hw"
;"ctl0" = "hw"


btw, when I try to run Unreal 2004 (linux version) I don't have sound in Unreal and xmms plays very cracked

---

### Post by soul_rebel on 2005-04-03
Some apps tend to access directly to sound card, preventing sounds from all other running applications.

To avoid this audio servers have been created, like esd, artsd, and jack. 
You can set up xmms to use a sound server instead of accessing the soundcard directly. 
Anyway there is a trick to launch an applications that wants to lock the soundcard just emulating direct access. It's a feature of the audio server (esd and artsd surely have it), any way i don't remember this command, so you'll have to find it out, and possibly post it here, so that usable knowlegde is built.

KDE uses artsd (usually) and gnome esd (usually)

bye

---

### Post by Severun on 2007-12-02
The way to do it is to get aoss or arts (I haven't tried esd), anyway, you just run the binary with the arts program.  It goes like this

artsd -d

This starts the arts daemon and the -d puts it into full duplex so you can use tihngs like TeamSpeak.

Then you run whichever application like:

artsdsp wine WoW.exe

or

artsdsp TeamSpeak

In programs like teamspeak it uses a shell script to launch the binary, artsdsp only works on binaries so you have to add the artsdsp call to the shell script itself so it runs on the binary.

I tried aoss, there is no server you just type

aoss TeamSpeak

I had problems with static w/ aoss so I use arts and it works beautifully.  I can run WoW under wine and I can run my streaming music player and teamspeak all at the same time!!! Woot.

My questions though is where do I go into cedega to tell it to launch Eve-Online  (or any other cedega game) With arts, aoss or some other audio sharing utility.

---

