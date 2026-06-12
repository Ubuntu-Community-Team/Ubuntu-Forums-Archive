---
title: "No Sound in wine 1.3.29"
date: 2011-10-20
forum: Wine
---

### Post by GodOfRandom on 2011-10-20
Hello.

Recently i tried wine 1.3.30 and had no problems with sound. However, after some time wine showed no audio drivers in audio tab and no Output/Input devices (Only "default").

I compiled wine 1.3.29 from source and still have no sound. And my audio tab looks a bit strange (maybe it is okay?).

Here is a screenshot.

And sorry me for my bad english.

---

### Post by ubupirate on 2011-10-20
It seems the devs at Wine removed the option to select audio driver sometime in the 1.3.2x range, not sure what version exactly.

1.3.30 uses winealsa.drv for audio, and the input/output devices as "default" will follow whatever devices you have active in sound preferences in Ubuntu.

At least that is how it works for me.

---

### Post by GodOfRandom on 2011-10-20
I had alsa listed in this tab in 1.3.30. After some time it changed to none and, if before i could chnge that default to something, now i cant change anything in audio tab. Same thing with wine 1.3.17, tried it too today.

---

### Post by GodOfRandom on 2011-10-22
Shameless bump.

---

### Post by Mad-Halfling on 2011-10-23
> **GodOfRandom said:**
> I had alsa listed in this tab in 1.3.30. After some time it changed to none and, if before i could chnge that default to something, now i cant change anything in audio tab. Same thing with wine 1.3.17, tried it too today.

I had this and just found a solution.

Just to make sure you've got a newer version of WINE, add the PPA
sudo add-apt-repository ppa:ubuntu-wine/ppa
then run 
sudo apt-get update
sudo apt-get upgrade
and this should get you to WINE 1.3.30+
then edit the ~/.wine/user.reg file, in there find the 
[Software\\Wine\\Drivers]
section (or just search for Drivers and set 
"Audio"="alsa"
that fixed it for me.  This will set up the driver in the audio tab of winecfg then you can (if necessary, my system was fine with the System Default options) tweak the audio devices

GL&HF
MH

---

### Post by jebblue on 2011-10-28
Mad-Halfling it worked for me too, thanks!

---

### Post by GodOfRandom on 2011-10-29
It doesn't work for me. I had OSS in that user.reg file (i think because i tried to set every driver in wine tricks after the sound loss). I set it to alsa and still have this.

BTW tried wine 1.3.17 again today. Sound works there, but still nothing in 1.3.29 and 1.3.30.

---

### Post by logan85 on 2011-11-16
I had the same problem, and i fixed in the following way:

I  uninstalled wine1.3, winetricks and wine1.3-gecko
after that I deleted the .wine directory from my home folder, and then reinstalled the wine, and now it works...

---

### Post by Bromden on 2011-11-16
Actually i think wine 1.3.30 is the best release. Before using it close every application that needs sound (firefox too), or they could go in conflict. Actually I've set STAC92xx Analog in wine config, and in the Multimedia Systems Selector i've set Automatic in the Default Output and Alsa in the Input.

I had the problem that Rage and Oblivion use different sound drivers (ALSA and OSS), with automatic now everything works fine.

Deleting the user.reg is another possible fix to Wine ALSA problems. You don't need to uninstall the entire program, just delete user.reg, and start Wine config, it will be auto-generated.

P.S. To add Multimedia System Selector in the System/Preferences activate it from the Edit Menus window.

---

### Post by ibates on 2011-11-25
> **GodOfRandom said:**
> 

And sorry me for my bad english.

Were my English as good as yours I would be more than happy - and it is my mother tongue.  Well done.

---

### Post by temporos on 2011-12-25
I'm experiencing a similar issue of no sound in Wine.  The Audio tab in Wine Config displays the following available audio drivers.
[list][*]ALSA Driver
[*]OSS Driver
[*]JACK Driver
[*]NAS Driver
[*]EsounD Driver[/list]

Selecting any combination of these drivers produces only a slight click or tap sound when tested (using the "test driver" button on the right), like it's trying to play a test sound, but gets cut off.  No applications running under Wine will play audio.  Anyone know what might be going on?

I've already tried deleting the "user.cfg" file in the ".wine" directory, but the problem persists.  I'm using Wine v1.2.2 (I think that's the latest stable release).

---

### Post by neigun on 2012-02-10
I would ditch 1.3.29.

Try installing this ppa: ppa:ubuntu-wine/ppa

Its currently on 1.4rc2 and works fine on Ubuntu 11.10, Gnome 3, etc.

The graphics and sound seems to be far better than on earlier versions. 

My kids  can now play Diablo II and Simcity 4!

TTFN

Neil

---

