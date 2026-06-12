---
title: "Workstation 8.0.4 NForce4 Audio"
date: 2008-07-29
forum: x86 64-bit Users
---

### Post by phenexfire on 2008-07-29
Howdy folks,

I have been playing around with this desktop version for a few days. I am thinking of going to it completely if I can find comparable apps to replace some of the ones I use in windows (already discovered WINE WOOT) but I have a question about nforce4 drivers.

First pc specs:
Mobo: Asus A8N-SLI Deluxe 64 Bit CPU: AMD 4200 dual core
Ram: 3 Gig
HDD: 80 gig master (Windows) / 160 gig slave (Ubuntu Workstation) / 300 gig Sata master (goodies drive)
5.1 Speaker system

I have hunted around for some nforce 4 chipset drivers so I can get the sound system working like it does in windows. but I only find some info
on nvidia site that I don't think will work on here.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
[http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

I tried seeing if I could use the linux drivers that are on the mobo support CD but it fails to make the kernal which I discovered many other people ran into something like that during the attempted install.

at the end of the attempt I found the log file for it, I will spare you the whole thing and paste the end comments in the log:

ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).

i have been hunting around for information but not much is out there it seems. I believe the alsa is being used at the moment and it just does not sound good. I have it set to use a 6 channel and had to duplicate front just to get the second set of fronts to work and the subwoofer and center are not getting anything at all.

Anyone got some suggestions or has anyone figured out how to solve this?
thanks for any help - suggestions.

---

### Post by mdsharp24 on 2008-07-29
Could you install lshw (apt-get update && apt-get install lshw) and then run: lshw -html > hardware.html

Then, look for your multimedia/audio information and paste please.

---

### Post by phenexfire on 2008-07-29
uhm I think this is what your after:

id:	
multimedia
description: 	Multimedia audio controller
product: 	CK804 AC'97 Audio Controller
vendor: 	nVidia Corporation
physical id: 	
5
bus info: 	
pci@0000:00:04.0
version: 	a2
width: 	32 bits
clock: 	66MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	Intel ICH
latency	=	0
maxlatency	=	5
mingnt	=	2
module	=	snd_intel8x0

---

### Post by mdsharp24 on 2008-07-29
Try [[COLOR="Blue"]This link[/COLOR]]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems") and make sure you have the latest kernel/module updates.

---

### Post by Yellow Pasque on 2008-07-29
If that doesn't work for you, try OSS4. (link in sig)

---

### Post by xinix on 2008-07-29
Theoretically the drivers for that chipset are part of the out of box installation for most distros.  Including the audio driver, but I'm not sure how complete it really is.  I only get sound on all channels when I'm watching a DVD.  The rest of the time it's stereo but my receiver shares the love with all the speakers.

---

### Post by phenexfire on 2008-07-30
I read over the information from the links provided OSS cost money to which I have none thanks to a crappy economy so I checked out the alsa information and that page is kind of confusing to me they way it is put together. It says to do one thing but if using something else do this command type stuff all over the place. 

I have been playing with Linux off and on but I am still pretty much a noob.
I did discover there was some sort of bug with the sound and someone mentioned turning all sliders to max so I checked that out and if I do that I can just barely hear a noise on the left set of speakers. =(

so I guess if someone can maybe just kinda spell it out on updating / installing some nforce4 drivers or point me to a page that is not so confusing that would be great. Sorry about the total noob thing. 

thanks:confused:

---

### Post by Yellow Pasque on 2008-07-30
OSS4 is free on Linux unless you have a Lynx Studio sound card (which you don't)

---

### Post by phenexfire on 2008-07-31
hmm I must have miss read something on the OSS pages then. It looked like they wanted money for the software. I will re-read it as well.

---

### Post by phenexfire on 2008-07-31
Hey Temujin,

I am following the OSS instructions but I stopped dead in my tracks becasue one of these commands says it will remove the gnome desktop?????

```
 sudo apt-get install esound esound-clients esound-common libesd0 libesd0-dev gstreamer0.10-esd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
esound-common is already the newest version.
The following extra packages will be installed:
  libaudiofile-dev
[B]The following packages will be REMOVED:
  libesd-alsa0 pulseaudio-esound-compat ubuntu-desktop[/B]
```

I don't want gnome to be removed, I assume that is what will happen here?

---

### Post by Yellow Pasque on 2008-07-31
As it says in the ubuntu-desktop package, this is a package that simply depends on the default packages in Ubuntu's configuration, one of which is alsa-base. I don't have this package installed and my system works perfectly fine.

It is safe to remove ubuntu-desktop

---

### Post by eln0k0fl on 2008-07-31
> **phenexfire said:**
> Howdy folks,

I have been playing around with this desktop version for a few days. I am thinking of going to it completely if I can find comparable apps to replace some of the ones I use in windows (already discovered WINE WOOT) but I have a question about nforce4 drivers.

First pc specs:
Mobo: Asus A8N-SLI Deluxe 64 Bit CPU: AMD 4200 dual core
Ram: 3 Gig
HDD: 80 gig master (Windows) / 160 gig slave (Ubuntu Workstation) / 300 gig Sata master (goodies drive)
5.1 Speaker system

I have hunted around for some nforce 4 chipset drivers so I can get the sound system working like it does in windows. but I only find some info
on nvidia site that I don't think will work on here.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
[http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

I tried seeing if I could use the linux drivers that are on the mobo support CD but it fails to make the kernal which I discovered many other people ran into something like that during the attempted install.

at the end of the attempt I found the log file for it, I will spare you the whole thing and paste the end comments in the log:

ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).

i have been hunting around for information but not much is out there it seems. I believe the alsa is being used at the moment and it just does not sound good. I have it set to use a 6 channel and had to duplicate front just to get the second set of fronts to work and the subwoofer and center are not getting anything at all.

Anyone got some suggestions or has anyone figured out how to solve this?
thanks for any help - suggestions.

I'm not sure what you mean by sound not "working like it does in windows", but I have the same rig you have and the 8.04 LTS AMD64drivers work just fine for me. If however, I try to build an optimized version with the latest kernel using kernelcheck, then the sound usually stops working.

---

### Post by phenexfire on 2008-07-31
eln0k0fl, I was comparing. Another words I have my rig working in windows and it sounds great and my 5.1 6 speaker system works but here in ubuntu I have to crank all the sound option sliders up just bearly hear a sound and when I say bearly I mean sticking the speaker up to my ear. and then onle 2 fronts are pushing anything at all.

=) thats all I meant.

---

### Post by phenexfire on 2008-07-31
ok here is my progress I have installed the OSS drivers per the directions on [http://ubuntuforums.org/showthread.php?p=4874981](http://ubuntuforums.org/showthread.php?p=4874981)
It detected the nForce 4 and generic usb audio device (beta)

I got the oss panel working and opened it up then loaded the music player that installed during ubuntu install picked an mp3 and fired it up. no sound. the vmix0-out had meter readings on the top right and the one on the lower left with rhythmbo. I then switched to spkmode SPREAD and the 2 rear left and right speakers played and the bass 2 front and center speakers had nothing. 

So this is about where I was with the alsa except that when i told it to duplicate front it used the 2 rear and 2 front and none of the volume sliders worked. 

So I have no idea what else to try.. I am going to see what happens if I use a different player I think, perhaps this one is not very good? I really don't know.

:(

---

### Post by phenexfire on 2008-08-02
No one has any idea's on how to fix this? perhaps ubuntu just can't handle a surround 6 Speaker 5.1 system and only a mono sounding 2 speaker setup?

---

### Post by phenexfire on 2008-08-03
alrighty then I guess no one has any idea how to get that working or ubuntu just can't handle a decent sound system. thanks for trying to help. I think I will go to another version of linux and hope that works. :confused:

---

### Post by eln0k0fl on 2008-08-03
The A8N32 SLI Deluxe uses a realtek AC97 sound chip. They have a linux audio driver at [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/). I haven't tried this yet, but why not give it a try?

---

### Post by Yellow Pasque on 2008-08-04
> I then switched to spkmode SPREAD and the 2 rear left and right speakers played and the bass 2 front and center speakers had nothing.

Try the latest version of OSS(4.1) It has vmix multichannel support built into ossxmix. Instructions for that can be found in the OSS4 thread.

---

