---
title: "Problem on installing Creative Soundblaster"
date: 2007-05-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by tL0z on 2007-05-30
Hello,

I've installed Ubuntu yesterday and, although my ATI 9600 XT works fine (I couldn't get it working fine with the previous versions), my sound driver doesn't work.
When I play a music or some kind of sound, the sound from the speakers is very "bass". 

How can I fix this?

Thanks

---

### Post by jusmurph on 2007-05-31
Double click the speaker icon in the top toolbar... Choose the device and tinker in there.

---

### Post by Unterseeboot_234 on 2007-05-31
Every time I do a new upgrade or re-install on the Linux, I have to tinker around with a patch or two from ALSA. Start out going to their Wiki Matrix chart. Add that patch, and the ALSA mixer from Add/Remove Ubuntu. The ALSA mixer will then have a volume control for each patch added from ALSA. I had the SB Live! card, it works good but you will never have the full capabilities of the SB Live! software to make special audio effects. That would take WINE (never tired that) to make your Linux run as a PC. I did however have 4 channel with the SB Live! and the ALSA Mixer.

Since then, I've gone over to another computer. I use the onboard nVidia soundchip on the graphics card. The ALSA patch made the volume and tone much richer.

**[[COLOR="Blue"]ALSA MATRIX CHART[/COLOR]]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Main")**

I'm waiting for the Ubuntu Audio/Video Suite to give me back some of the functionality of the SB Live! and that requires Fiesty.

Good luck, hope this helps.

---

### Post by tL0z on 2007-05-31
Sorry for my *noobness* but I didn't understand what to do. :(

I searched for ALSA on Synaptic and I found a lot of stuff. How do I know what do I have to install?

By the way, I have a SB Audigy.

---

### Post by Unterseeboot_234 on 2007-05-31
OK, I'll concede sound can be a pain in Linux. First, sorry about my previous post. It was for an ALSA wiki that is totally new, totally incomplete. From there I followed a link to the original ALSA web site to look at their Soundcard Matrix. There were 3 or 4 models of SB Audigy. Only the model in the notebook is known to work. But, then again, this ALSA page list is old information. Here is the link to your soundcard (for reference or for interest)

[**[COLOR="RoyalBlue"]ALSA Soundcard Matrix for Creative Labs[/COLOR]**]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix")

Comment: this page shows you CAN build a module, then go crazy trying to install as a kernel mod, or as a module with a folder inside another folder inside another folder.... we're not at that point yet, but I've been there, doing just that, trying to noob my way through.

I then go into Synaptic trying to remember which mixer. That reminds me that Ubuntu does come with a wide range of the ALSA modules already installed. That's good to know. I would advise installing AlsaMixerGUI, but wait...

Try this link first. I found it searching the Forums from the Forums Home level.

**[COLOR="Blue"][Comprehensive SoundCard Guide]("http://ubuntuforums.org/showthread.php?t=205449")[/COLOR]**

Do the SoundGuide recommendations for discovering if your Ubuntu sees hardware and then the dev/ (if any) it has installed.

This type of approach will give information to the Techies on this board that can help us try to help you.

One final note. midi without an external box just plain Sucks in ubuntu Drake. java can run midi w/o any problem. ubuntu Drake needs a clock change and a soft server that just takes over the computer resources. To playback midi, use a java media player program. (but that's another problem after you get your soundcard working). To record midi, get an external box or Fiesty and Ubuntu Studio. Again, after we can hear your soundcard.

---

### Post by tL0z on 2007-05-31
I did it!! :D

I muted the Audigy Analog/Digital Output Jack.

Thanks for your help. ;)

---

