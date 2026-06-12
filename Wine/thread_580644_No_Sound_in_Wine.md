---
title: "No Sound in Wine?"
date: 2007-10-18
forum: Wine
---

### Post by constchar* on 2007-10-18
I was running Wine 0.9.46 compiled from sources and everything was
fine and dandy but then I decided to upgrade to Wine 0.9.47,
I did a "make uninstall" with the 0.9.46 then did the "./tools/wineinstall"
and since then I'm getting no sound in any Wine apps, including winecfg.

Selecting ALSA or OSS both result in "Audio test failed" when I click
the "Test Sound" button.

I get this output:
"fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported."

I should probably also note that at one point Counter-Strike: Source
made some menu sounds but after that I didn't hear anything.

Thanks for any help.

---

### Post by cogadh on 2007-10-19
If you are referring to the test sound button in winecfg, that is not functional yet. Any particular reason you compiled from source and didn't use the precompiled Ubuntu package?

---

### Post by constchar* on 2007-10-19
Every time I've used the "Test Sound" button it's always made a
type of a drum sound (not sure how else to explain the sound).

I wasn't aware the precompileds were up to date with the latest version so I'll check that out.

---

### Post by constchar* on 2007-10-19
I switched over to the binaries and even then I still get the same problem,
failed audio test and no audio from any Windows applications.

The only sound driver that works is EsounD but that outputs
laggy sound and sometimes it's cracky and poppy.

---

### Post by cogadh on 2007-10-19
Ah, nvm, I was thinking of the Control Panel button, not the test sound button. 

Does sound work through ALSA in any native apps?

---

### Post by constchar* on 2007-10-19
Yes, including KDE and VideoLAN which I use frequently.
I should probably note I'm using Feisty Fawn and haven't
upgraded to Gutsy Gibbon yet although the update manager is ready
to run the update but I'm not sure if I want to do that just yet.

---

### Post by victor9098 on 2007-10-28
Hi,

I am having a similar problem. When I try to run a game i get a message saying there will be no voice or sound since the system does not support DirectSound. (Code = 1.0).

Installed WINE via Synaptic, everything else seems to be fine with it.

Any suggestions would be great!

---

### Post by victor9098 on 2007-10-28
Hi,

I am having a similar problem. When I try to run a game i get a message saying there will be no voice or sound since the system does not support DirectSound. (Code = 1.0).

Installed WINE via Synaptic, everything else seems to be fine with it.

Any suggestions would be great!

---

### Post by Crafty Kisses on 2007-10-28
I've had the same problem, but I did a sound test, and it appeared to be working, so I don't really know. :(

---

### Post by TempestSA on 2007-11-23
I have a similar problem, I've never had sound working in Wine. 

I've gone on the audio tab in  winecfg, not matter what driver I select (ALSA, OSS, JACK, NAS) or level of Hardware acceleration I get an error when I click on Test Sound (Audio Test Failed). I have checked and unchecked Driver Emulation. Are there any logs I can view to see what the error is? 

I've never had problems with the sound in any other application, besides the mic not working in Ubuntu and midi being garbled in Hydrogen. 

I've got a Dell Inspiron 6400.

Thanks

---

### Post by Bram-NL on 2007-12-26
As I posted [over here]("http://ubuntuforums.org/showthread.php?p=4015871#post4015871"):

**Great news!** I got it working! :)

What I did is using the latest binaries from [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb). So the steps to take are:

[LIST]
_Add the repository to Ubuntu:_
[*]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -


[*]**For Ubuntu Gutsy (7.10)**:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list


[*]**For Ubuntu Feisty (7.04)**:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list


_And at last, install or upgrade Wine:_
[*]**If you *don't* have Wine installed yet**:
sudo apt-get update && sudo apt-get install wine


[*]**If you have Wine *already* installed**:
sudo apt-get update && sudo apt-get upgrade
[/LIST]

That's it :)

---

### Post by needhelpplease on 2008-04-12
I'm having the same problem.  I'm using the Wine from that repos.  Sound worked for a while but seemed to stop working a couple of versions ago.  Any ideas?

---

### Post by heatpumpcontrol on 2008-05-22
I wasn't getting any sound so I tried the reinstall from the repos and it worked. I get sound no matter which driver I select in the wine-config sound tab. Try it.....it helped me and I hadn't had sound since my 8.04 fresh install.

update:

It stopped working....while in Alsa mode. I switched to Esound and Emulation and it seems to be stable. I will log out and back in and if it fails I'll report back if not... then it is staying active.

---

### Post by Coolit on 2008-05-23
I have the same problem, it was working using the ALSA driver with the Hardy deb then just "stopped working".

I've yet to investigate as I don't use wine that much. I'm using an Asus xona sound card.

---

### Post by matty47 on 2008-06-22
@ heatpumpcontrol Thanks for the tip. I did likewise and Used ESound and emulation and the sound in wine now works!!
Matthew

---

### Post by Tekovro on 2008-07-13
> **matty47 said:**
> @ heatpumpcontrol Thanks for the tip. I did likewise and Used ESound and emulation and the sound in wine now works!!
Matthew

Thanks, that worked for me too!

---

### Post by zft on 2008-07-24
I've had quite a strange expirience with wine - the sound didn't work by default (I've got a GA-P35-DS3 gigabyte motherboard with a Realtek ALC889A Audio), so I tried the solution above - use esound and emulation. Everything worked, though the "check sound" button still reported an error. Afterwards, I desided to check the other modes, and surprisingly, the default ALSA with no emulation worked fine.

So, I would advise everyone to try differnet modes even if the test sound button doesn't work, the sound might actually work in the emulated programs. Also, try ESound and emulation first.

P.S. used wine 1.1.1 from the official site.

---

### Post by vixo7 on 2008-08-01
I had the same problem with my USB audio. This worked for me: [http://ubuntuforums.org/archive/index.php/t-380852.html](http://ubuntuforums.org/archive/index.php/t-380852.html)

The idea is to comment a line in file: /etc/modprobe.d/alsa-base
The line to comment is:

#options snd-usb-audio index=-2

This allowed my system to recognize the USB audio. Now iTunes on Wine works and also Amarok.

Good luck.

---

### Post by phoenix116 on 2008-09-05
> **zft said:**
> I've had quite a strange expirience with wine - the sound didn't work by default (I've got a GA-P35-DS3 gigabyte motherboard with a Realtek ALC889A Audio), so I tried the solution above - use esound and emulation. Everything worked, though the "check sound" button still reported an error. Afterwards, I desided to check the other modes, and surprisingly, the default ALSA with no emulation worked fine.


i have the same problem with my creative audigy card - sometimes it works and then it suddenly stops working - enabling Esound with emulation, apply, and then switch back to alsa normal mode always works for a while.

but every time i do this, the registry settings for my wc3 seem to be reset, no clue why..

---

### Post by spongypants23 on 2008-09-19
I can't find the ESound thing.

---

### Post by harrison3001 on 2008-11-23
I found a way installing all related esound files and setting the sound preferences to PulseAudio sound server or ESD. Hope it helps.

---

### Post by opt1k on 2009-08-07
Hi. 
Try selecting "ALSA" only. Full acceleration. uncheck emulate driver
click ok
exit wincfg
open winecfg
try "test audio" again

---

### Post by mskogly on 2010-01-16
Can someone confirm that it is impossible to get sound from bot software running under wine and native linux apps at the same time? That is my problem right now. I can get sound som the test button and from spotify as long as no other software is running. Irritating as hell.

---

### Post by Pikestaff on 2010-01-17
> **mskogly said:**
> Can someone confirm that it is impossible to get sound from bot software running under wine and native linux apps at the same time? That is my problem right now. I can get sound som the test button and from spotify as long as no other software is running. Irritating as hell.

I have never had an issue hearing the sound effects from WoW on Wine and having Amarok running concurrently (so long as I am using the ALSA driver... anything else makes me unable to hear sound from both)

---

### Post by mskogly on 2010-01-17
Got it to work by selecting the Esound instead of oss and alsa.

---

### Post by skewray on 2010-09-08
Yesterday I was running wine under lucid/kde and the sound worked fine.  I installed the gnome and xubuntu desktops just to check them out, logged into gnome, logged back into kde, and after this wine no longer had any sound.

The kmix settings and the wine sound settings appear unchanged.  Wine is using the default of ALSA.  Any suggestions?

---

### Post by MrAntonB on 2011-07-15
> **mskogly said:**
> Got it to work by selecting the Esound instead of oss and alsa.

Thank you so much, I've been fighting with it for the past few hours. This worked pefectly! :popcorn:

---

