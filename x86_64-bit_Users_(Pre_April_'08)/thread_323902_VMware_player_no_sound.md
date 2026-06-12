---
title: "VMware player no sound"
date: 2006-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Burkey on 2006-12-22
I am trying to get vmware player running on my wifes new Turion64 x2 laptop.  She only needs it to watch DRM streams from the internet on windows (Thanks Ms you big A-holes for destroying freedom on my computer)

VMPlayer runs fine, windows installed and the vmtools are loaded, the soudcard appears happy and I can hear sound fine in Linux.  I do not get any errors on launch of vmplayer about not being able to access /dev/dsp or anything similar.

Windows seems to "think" sound is ok and plays back files but I can hear nothing.  I have adjusted volumes up to max, muted/unmuted etc.

I am really hoping someone can please help with this as it is now the only problem she has and accounts for half of what she does on her laptop... and I am stumped.  Not to mention frustrated!

---

### Post by Spano on 2006-12-23
Configuring Sound
VMware Server provides a sound device compatible with the Creative Technology
Sound Blaster Audio API adapter and supports sound in Windows 95, Windows 98,
Windows Me, Windows NT, Windows 2000, Windows XP, Windows Server 2003, and
Linux guest operating systems. The VMware Server sound device is disabled by default
and must be installed using the virtual machine settings editor (VM > Settings).
Sound support includes PCM (pulse code modulation) output, and input. For example,
you can play .wav files, MP3 audio, and Real Media audio. MIDI output from Windows
guests is supported through the Windows software synthesizer. MIDI input is not
supported, and no MIDI support is available for Linux guests.
Windows 2000, Windows XP, and most recent Linux distributions automatically detect
the sound device and install appropriate drivers for it.

---

### Post by Burkey on 2006-12-23
Thanks for the reply Spano, however I am using vmplayer not vmserver.  I have already installed the vmware tools which then enables audio.  The audio device is listed, but it will not make any sound.

On my other computers this has worked flawlessly, which is why I am suspecting something in Edgy/amd64 since it is fine on Edgy/32-bit

Is there some way I can monitor or ensure the /dev/dsp device is free?  I have tried killing off esd but it makes no difference and normally on other installs the player shows a big X on the sound card if it is in use by the host OS.

---

### Post by Spano on 2006-12-23
Sorry, didn't notice Player.
> Is there some way I can monitor or ensure the /dev/dsp device is free?
found this
```
# fuser /dev/dsp
```
output will be a PID number or nothing at all if no devices.

---

### Post by puccaso on 2007-01-14
ok
well i did the fuser thingi
and it doesnt show anything

i tried when i opened vmplayer and the initial error message came up
then i tried when vmplayer xp wsa up and running
adn still fuser showed nothing
on both accounts


any ideas?

---

### Post by davea402 on 2007-02-01
hey guyz

i use to get the same error with the /dev/dsp device currently in use and etc.  this website below will take u to vmware community i think and within the posts it will tell you to download a file and run it.


[http://www.vmware.com/community/thre...7101&tstart=60](http://www.vmware.com/community/thre...7101&tstart=60)

to start vmware i used vmwareesd

i am using ubuntu 6.06 and guest system windows xp all on dell 9300 inspiron....

hope it helps guyz

---

### Post by stuntman84 on 2007-07-30
the link posted above is outdated...please post updated link....I m having similar issue...no sound device is installed when i run XP as guest on my host ubuntu Feisty OS.
Any help will be much appreciated.
thank you

---

### Post by d_xtremw on 2007-10-19
Im using vmware server on feist and im having the same problem. the difference is that i went to vm--> settings and there is no option there to enable sound through the vm (at least none that i can see). any help with this?? (also it duznt recognize any usb device through the vm but thatws a different matter i guess.)

---

### Post by iammeagain on 2008-01-05
I was hoping to find a fix to a similar problem. I was trying to get amsn to do a video call when i found out it is not yet supported. Anyways i messed up my audio settings so now Vmware wont play. I figured i could edit the .vmx file to update it with new audio settings, if i knew what those were.

i have mine fairly well organized and here is the audio section from my .vmx file.```

####
#Audio
####

sound.present = "TRUE"
sound.virtualDev = "es1371"
sound.fileName = "-1"
sound.autodetect = "TRUE"
sound.pciSlotNumber = "-1"

```


related links i found:
[http://communities.vmware.com/thread/69875](http://communities.vmware.com/thread/69875)
[http://communities.vmware.com/thread/62335](http://communities.vmware.com/thread/62335)
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_run_Windows_with_VMware_Player_in_Linux_for_free](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Howto_run_Windows_with_VMware_Player_in_Linux_for_free)

I have had no luck so far, but maybe those links will help someone. I think I need to run that part of the install for player that configures everything and have it rediscover my audio.

---

### Post by iammeagain on 2008-01-05
I tried running```
sudo vmware-config.pl 
``` But it didn't do anything for the audio. i also tried different ways of setting up the audio for the .vmx file. Maybe I will just have to go with a full reinstall of VMware player I have to have the sound because I use it for video calling on MSN messenger.

---

### Post by VMan on 2008-01-06
> also it duznt recognize any usb device through the vm but thatws a different matter i guess.

I have this problem also.  I will start another thread on it.  Sorry I can't help with the sound.  Sound is working for me (two seperate instances of XP guest.

---

### Post by iammeagain on 2008-01-06
My audio was actually messed up for my whole system I figured out. But it still doesn't work on one virutal system. 
Make sure there are no audio programs running in the background, because that won't allow vmware to take control of the audio device, just a tip incase you haven't checked that.

---

